# R提取图片的文本
## 主要函数
```{r}
ocr(image, engine = tesseract("eng"))
tesseract(language = NULL, datapath = NULL, options = NULL,cache = TRUE)
```
参数：
image 图片文件路径，支持png、tiff、jpeg等格式
engine tesseract引擎，通过函数tesseract()来创建
language 训练数据的语言字符简写，默认为英语（eng）
datapath 训练数据的路径，模型为系统库
options tesseract引擎的相关参数，默认为NULL，可查看文档
cache 可以使用训练数据的缓存版本，默认为TRUE

3.tesseract_download(lang, datapath = NULL, progress = TRUE) #下载训练数据
4.tesseract_info() #查看训练数据路径、可使用数据的语言格式、当前版本

参数：
lang 训练数据的语言格式简写，比如英语就是eng，可查看tessdata repository.
datapath 训练数据下载路径地址
progress 下载中，是否要输出下载进程，默认为输出

```{r}
#英文
install.packages('tesseract')
library('tesseract')
setwd('e:/tess') # 设定工作路径
tesseract_info() #查看当前可用语言格式
text_1<-ocr('e:/tess/eng_1.jpg', engine = tesseract("eng"))
cat(text_1) #输出结果

#中文
tesseract_info() #先查看是否有中文训练数据，如果没有，需要下载安装
tesseract_download("chi_tra")
tesseract_download("chi_sim") #chi_sim和chi_tra均是中文训练数据
text<-ocr('e:/tess/chi_1.jpg', engine = tesseract("chi_sim"))

#批量提取图片
emp<-list.files(pattern='*.jpg')  #处理默认路径下jpg格式图片
text<-ocr(temp, engine = tesseract("chi_tra"))
cat(text)

```

```html
<div>  https://blog.csdn.net/sinat_26917383/article/details/54487359  </div>
```
