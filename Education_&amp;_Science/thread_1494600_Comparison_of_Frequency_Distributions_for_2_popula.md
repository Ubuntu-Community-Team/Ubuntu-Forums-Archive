---
title: "Comparison of Frequency Distributions for 2 populations (unpaired data)"
date: 2010-05-27
forum: Education &amp; Science
---

### Post by ugm6hr on 2010-05-27
I use gretl for basic statistical analysis.

I have 2 independent, but comparable populations with continuous data. 

I want to create a graph of the 2 data sets with the same scale, so that they can be placed one above the other, to allow visual comparison of the 2 groups distributions.

I have attached examples of the individual population plots, as given by gretl.

gretl does not appear to allow fine tuning of the x scale - is it possible?  I'd like to have the scales identical on the 2 plots.

If not, would anyone mind pointing me towards the necessary detail to do this with another apllication?  I know R is powerful, but have never used it, and have only basic statiscal background.

---

### Post by spinoza666 on 2010-05-27
Don't know anything about gretl, but if you wanna try out R, here goes. I'm assuming you have your data in two columns in a tab-delimited text file, let's call them x and y.

```

sudo apt-get install r-base #Install R

R                           #Start R and load data

data<-read.table('/home/username/somefolder/data.txt',header=T)

pdf()                       #Telling R you wanna make a pdf

par(mfrow=c(2,1))           #Partitioning the output window and plotting

hist(x,xlim=c(floor(min(x,y)),ceiling(max(x,y))), xlab='Black', main='Some main title') 

hist(y,xlim=c(floor(min(x,y)),ceiling(max(x,y))), xlab='White',main=' ')

dev.off() #R will print the output in whatever directory your in


```

Ah that was a nice break from exams:)
Did it work?

---

### Post by spinoza666 on 2010-05-27
Oh sorry,

wherever it says x or y, you need to put in data$x and data$y instead.

---

### Post by ugm6hr on 2010-05-28
Sorry to interupt your exam plans!

Unfortunately, I've fallen at the first hurdle....

I have a tab-delimited list with 2 columns, with the top (label) row now as:
```
x          y
210        203
etc
```

But the first line won't load my data:
```
data<-read.table('/media/sdhome/male.txt',header=T)
Error in scan(file, what, nmax, sep, dec, quote, skip, nlines, na.strings,  : 
  line 606 did not have 2 elements

```

This appears to relate to the fact that the 2 data sets are not paired (i.e. they are independent) - one group (white) has 605 data points, with 814 in the other (black). The data being measured is the same (time), but separated into Black and White - would it be better to have the data as a single column of 1421 data points with 2 values - time and colour?

---

### Post by spinoza666 on 2010-05-28
Well, I think it should work if you put a 'fill=TRUE' within the read.table command. It should then fill in blank rows in the shorter row.

---

### Post by frncz on 2010-05-28
Would this not be an easy task in gnumeric or openoffice spreadsheet?

---

### Post by spinoza666 on 2010-05-28
I would think so, but so much more fun in R:)

---

### Post by ugm6hr on 2010-05-28
Ok... Seem to be getter there.

```
data<-read.table('/media/sdhome/LQT_Athletes/male.txt',header=T,fill=TRUE)

pdf()                     

par(mfrow=c(2,1))        

hist(data$x,xlim=c(floor(min(260,260)),ceiling(max(520,520))), xlab='Black', main='Some main title') 

hist(data$y,xlim=c(floor(min(260,260)),ceiling(max(520,520))), xlab='White',main=' ')

dev.off()
```

Still need a couple of things...

1. Can I get a jpg / png instead of pdf?
2. Will it plot a normal distribution on top of each frequency-density plot using the calculated mean/sd?
3. How can I control the width of the histogram bars (I would like them at 10, as my original - R seems to have used 20)?

---

### Post by ugm6hr on 2010-05-28
> **frncz said:**
> Would this not be an easy task in gnumeric or openoffice spreadsheet?

I'll give that a go too.

EDIT: I can't see that either can draw a normal distribution curve to fit the data. This is important for my final result.

---

### Post by spinoza666 on 2010-05-28
> **ugm6hr said:**
> Ok... Seem to be getter there.

```
data<-read.table('/media/sdhome/LQT_Athletes/male.txt',header=T,fill=TRUE)

pdf()                     

par(mfrow=c(2,1))        

hist(data$x,xlim=c(floor(min(260,260)),ceiling(max(520,520))), xlab='Black', main='Some main title') 

hist(data$y,xlim=c(floor(min(260,260)),ceiling(max(520,520))), xlab='White',main=' ')

dev.off()
```

Still need a couple of things...

1. Can I get a jpg / png instead of pdf?
2. Will it plot a normal distribution on top of each frequency-density plot using the calculated mean/sd?
3. How can I control the width of the histogram bars (I would like them at 10, as my original - R seems to have used 20)?

In reply to:

1. Yes, exchange pdf() for jpeg() or png()
2. No, but it's possible although a bit complicated:
[http://tolstoy.newcastle.edu.au/R/help/06/08/32600.html]("http://tolstoy.newcastle.edu.au/R/help/06/08/32600.html")
3.Yes, issue a breaks=somenumber within the hist command.

Sorry, but gotta get back to studying for the mother of all exams....

---

### Post by hubie on 2010-05-28
> **ugm6hr said:**
> 
1. Can I get a jpg / png instead of pdf?
Easy.  To see what types you can do, check out the help: 
```
?png
```
It will show you how you can do bmp, jpg, png, and tiff.
> **ugm6hr said:**
> 2. Will it plot a normal distribution on top of each frequency-density plot using the calculated mean/sd?
Check out [this paper]("http://cran.r-project.org/doc/contrib/Ricci-distributions-en.pdf") on fitting distributions.  In particular, look at page 16 (the code for that plot is on page 15).
> **ugm6hr said:**
> 3. How can I control the width of the histogram bars (I would like them at 10, as my original - R seems to have used 20)?
Check out the help for the histogram function:
```
?hist
```
I believe the parameter you are interested in is "breaks," and some examples are given.  Another helpful page is [here]("http://msenux.redwoods.edu/math/R/hist.php").

---

### Post by ugm6hr on 2010-05-29
Thanks all... I think I clearly need to start using R more!  Apologies in advance for any future help I ask for.

My final script 
```
# Import data in columns (header = top row)
b<-read.table('/media/sdhome/black.txt',header=T,fill=TRUE)
w<-read.table('/media/sdhome/white.txt',header=T,fill=TRUE)
bf<-read.table('/media/sdhome/blackf.txt',header=T,fill=TRUE)
wf<-read.table('/media/sdhome/whitef.txt',header=T,fill=TRUE)

#Divide into 4 plot areas vertically
par(mfcol=c(4,1))

# Draw histogram b
hb<-hist(b$b,xlim=c(floor(min(300,300)),ceiling(max(500,500))),ylim=c(floor(min(0,0)),ceiling(max(160,160))), xlab='BM',main=' ',breaks=15,col="beige")

# Create N distribution plot to match
bxfit<-seq(min(300),max(500),length=40)
byfit<-dnorm(bxfit,mean=mean(b$b),sd=sd(b$b))

byfit <- byfit*diff(hb$mids[1:2])*length(b$b) 

# Create N distribution for histogram w
wxfit<-seq(min(300),max(500),length=40)
wyfit<-dnorm(wxfit,mean=mean(w$w),sd=sd(w$w))

wyfit <- wyfit*diff(hb$mids[1:2])*length(b$b) 

lines(bxfit, byfit, col="red", lty=1, lwd=2)
# lines(wxfit, wyfit, col="blue", lty=2, lwd=2)

# Draw 2nd histogram w
hw<-hist(w$w,xlim=c(floor(min(300,300)),ceiling(max(500,500))),ylim=c(floor(min(0,0)),ceiling(max(160,160))), xlab='WM',main=' ',breaks=15,col="beige")

# Create N distribution to fit w
bxfit<-seq(min(300),max(500),length=40)
byfit<-dnorm(bxfit,mean=mean(b$b),sd=sd(b$b))

byfit <- byfit*diff(hw$mids[1:2])*length(w$w) 

wxfit<-seq(min(300),max(500),length=40)
wyfit<-dnorm(wxfit,mean=mean(w$w),sd=sd(w$w))

wyfit <- wyfit*diff(hw$mids[1:2])*length(w$w) 

# Draw N distributions
lines(wxfit, wyfit, col="blue", lty=1, lwd=2)
# lines(bxfit, byfit, col="red", lty=2, lwd=2)


# Draw histogram bf
hbf<-hist(bf$b,xlim=c(floor(min(300,300)),ceiling(max(500,500))),ylim=c(floor(min(0,0)),ceiling(max(20,20))), xlab='BF',main=' ',breaks=15,col="grey")

# Create N distribution plot to match
bfxfit<-seq(min(300),max(500),length=40)
bfyfit<-dnorm(bfxfit,mean=mean(bf$b),sd=sd(bf$b))

bfyfit <- bfyfit*diff(hbf$mids[1:2])*length(bf$b) 

# Create N distribution for histogram w
wfxfit<-seq(min(300),max(500),length=40)
wfyfit<-dnorm(wfxfit,mean=mean(wf$w),sd=sd(wf$w))

wfyfit <- wfyfit*diff(hbf$mids[1:2])*length(bf$b) 

lines(bfxfit, bfyfit, col="brown", lty=1, lwd=2)
# lines(wfxfit, wfyfit, col="purple", lty=2, lwd=2)

# Draw 2nd histogram w
hwf<-hist(wf$w,xlim=c(floor(min(300,300)),ceiling(max(500,500))),ylim=c(floor(min(0,0)),ceiling(max(50,50))), xlab='WF',main=' ',breaks=15,col="grey")

# Create N distribution to fit w
bfxfit<-seq(min(300),max(500),length=40)
bfyfit<-dnorm(bfxfit,mean=mean(bf$b),sd=sd(bf$b))

bfyfit <- bfyfit*diff(hwf$mids[1:2])*length(wf$w) 

wfxfit<-seq(min(300),max(500),length=40)
wfyfit<-dnorm(wfxfit,mean=mean(wf$w),sd=sd(wf$w))

wfyfit <- wfyfit*diff(hwf$mids[1:2])*length(wf$w) 

# Draw N distributions
lines(wfxfit, wfyfit, col="purple", lty=1, lwd=2)
# lines(bfxfit, bfyfit, col="brown", lty=2, lwd=2)

```

I then exported as svg (rkward allows this to be done with a few clicks), and edited the appearance with Inkscape for the final labels (excluded from the attached picture).

Thanks again!

---

### Post by R33D3M33R on 2011-02-18
I need help with almost the same thing. I would like to plot 2 histograms with pdf's on top of the histogram, but i get the picture as shown in attachment. So, what's wrong with the pdf's? If i draw them on separate graph, everything works. Thanks for the help in advance!

Here is the code:

```

par(mfcol=c(2,1))

h1 <- hist(Data$V1,scale="frequency", col="darkgray", xlab="Time per km")
.x <- seq(min(0), max(5), length=100)
g1 <- length(Data$V1)*dgamma(.x, shape=1.312491, scale=0.795368)
remove(.x)
lines(g1,col="red")

h2 <- hist(Data$V1,scale="frequency", col="darkgray", xlab="Time per km")
numSummary(Podatki[,"V1"], statistics=c("mean", "sd", "quantiles"), 
  quantiles=c(0,1))
.x <- seq(min(0), max(5), length=100)
g2 <- length(Data$V1)*dgamma(.x, shape=2.632, scale=1.59542)
remove(.x)
lines(g2,col="purple")

```


P.S: attaching png's doesn't seem to work, so here is the picture:

[[IMG]http://img218.imageshack.us/img218/9622/histb.png[/IMG]](http://imageshack.us/photo/my-images/218/histb.png/)

---

### Post by PGScooter on 2011-02-18
I don't know what's wrong, but in case you can't figure it out, maybe you could figure it out with ggplot2, which makes graphs in R a lot easier.

---

### Post by R33D3M33R on 2011-02-19
I solved this by changing:
```

remove(.x)
lines(g1,col="red")

```

to:

```
lines(.x,g1,col="red")
remove(.x)
```

---

