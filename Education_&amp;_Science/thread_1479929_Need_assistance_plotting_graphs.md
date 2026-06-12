---
title: "Need assistance plotting graphs"
date: 2010-05-11
forum: Education &amp; Science
---

### Post by Ceenap on 2010-05-11
This might be a long post so bare with me. Aren't too handy with Linux but am getting the hang with it after having used it in a few courses and so. Anyway, we are doing a work where we test the load on servers and we use /proc to get data we need from it. We use bash scripts to get the info we need so for example we take out the cpu usage level every tenth second and save it to a file.

For example the text file with cpu usage can look like this
```
09:58:13 51%
09:58:23 51%
09:58:33 46%
09:58:43 25%
09:58:54 51%
09:59:04 52%
09:59:14 51%
09:59:24 51%
09:59:34 51%
09:59:44 51%
09:59:54 51%
10:00:04 55%
10:00:14 51%

```Now what we need to do is plot this up nicely, like the time on the x-axis and cpu % on the y-axis. We have tried some programs. First Grace (xmgrace) where the problem seems to be that it can't handle the HH:MM:SS format but from what we have found it actually should. Seems like in the predecessor xmgr you could write something like @format MMDDYYHMS to let it know what format it is. Could easily remove the % sign anyway. 
Then tried openoffice spreadsheet which is sort of ok, though the x-axis in kind of cluttered when using the Line chart type and the axis can't be changed then, only if it's a XY type and then the x-axis doesn't show correct values. Have tried xgraph in the past and it worked with just x and y values without strange time formatting. 

So yeah we are using Ubuntu 9.10 and are wondering if there are any sort of easy way to easily plot these values nicely and being able to like set intervals in the x-axis so that not every 10 sec value is shown. I think it's the handling of the time format that is making it difficult.

Hope you understand what I'm trying to do and would be grateful for any help.

---

### Post by hubie on 2010-05-11
Here is a quick way to do it in R (use this as a starting point):

```
# Set up the output pdf file
pdf("mydata.pdf")
# Read the data
data <- read.table("mydatafile.txt",sep="")
# Name the columns
names(data) <- c("time","pct")
# Convert the time column into a time data type
t <- strptime(data$time, "%H:%M:%S")
# Strip off the last character (percent sign)
pct <- strtrim(data$pct, 2)
# Plot it up
plot(t,pct,pch=16,col='blue',type='b',xlab="Time",ylab="Percent")
title("CPU Usage")
# Close the pdf file
dev.off()
```

I've attached the output I get.

---

### Post by Ceenap on 2010-05-11
Thank you, during my search for plotting programs R came up but I never looked more into it. Some of our files has a slightly different look to it but trying your script it worked for this bit and I can possibly just modify it to make those work as well. It's a good start and I thank you again!

---

### Post by tgalati4 on 2010-05-11
sudo apt-get install gnuplot
man gnuplot

gnumeric also does decent plots.

sudo apt-get install gnumeric
gnumeric

---

### Post by hubie on 2010-05-11
> **Ceenap said:**
> Thank you, during my search for plotting programs R came up but I never looked more into it. Some of our files has a slightly different look to it but trying your script it worked for this bit and I can possibly just modify it to make those work as well. It's a good start and I thank you again!

Making nice plots is what led me to R.  It has nice utilities to easily input and output data, and I like the easy handling of time data as well.  Lots of really good tutorials and other documentation available.  Some nice sites to get you going are:

[R Programming/Graphics]("http://en.wikibooks.org/wiki/R_Programming/Graphics")
[R Graph Gallery]("http://addictedtor.free.fr/graphiques/thumbs.php?sort=votes")

---

### Post by Ceenap on 2010-05-11
> **tgalati4 said:**
> sudo apt-get install gnuplot
man gnuplot

gnumeric also does decent plots.

sudo apt-get install gnumeric
gnumeric

Also thanks for these. Gnumeric does sort of what openoffice spreadsheet did, but this program actually lets me edit the axis and so on. Pretty much what we were looking for. Thanks again for quick response.

---

### Post by earlycj5 on 2010-05-12
> **Ceenap said:**
> Also thanks for these. Gnumeric does sort of what openoffice spreadsheet did, but this program actually lets me edit the axis and so on. Pretty much what we were looking for. Thanks again for quick response.

Not to be pedantic, but R will allow you to edit the axis as well, it's extremely flexible in it's graphical output as well.

---

