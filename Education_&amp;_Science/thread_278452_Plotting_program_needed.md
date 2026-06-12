---
title: "Plotting program needed"
date: 2006-10-16
forum: Education &amp; Science
---

### Post by basilwatson on 2006-10-16
Hi all 
Im after a simple graphing program. I use Z grapher in windows and would like to find one for Linux 

 What I would like is a program where I could type in the x and Y co ordinates and then click on a button to get the regression ,and to find the equation 

Also the area under the graph,

I have been looking , but for example Kplot ( all the ones I have looked at) are not . well I couldnt find out how to enter in the data lets put it that way !

I tried grace. but ot wouldnt load for me 

Any Ideas??

Kind regards

Stephen

---

### Post by girishv on 2006-10-16
If you dont mind little typing, you can use gnuplot, its a very simple interactive plotting package.

---

### Post by didobuntu on 2006-10-16
+ 1

With gnuplot you can export your result in postsript file, tex files, fig files.

You can also integrate them under LateX using epsfig or PSFRAG for example.

---

### Post by roderikk on 2006-10-16
Yes, gnuplot is what you are looking for.

This is a site with examples I often use:

[http://t16web.lanl.gov/Kawano/gnuplot/plot1-e.html](http://t16web.lanl.gov/Kawano/gnuplot/plot1-e.html)

Good luck!

---

### Post by basilwatson on 2006-10-16
Ive downloaded gnuplot , but the command line looks daunting ..any with a GUI  ,,,
With Zgrapher for example I click Xy type in the info then click regression  /dy/dx and there is the result ... I have use it a lot for what if ... so whange /compare data a lot ..

So the quicker and easier to use ..the better 

Stephen

---

### Post by akniss on 2006-10-16
> **basilwatson said:**
> Ive downloaded gnuplot , but the command line looks daunting ..any with a GUI  ,,,
With Zgrapher for example I click Xy type in the info then click regression  /dy/dx and there is the result ... I have use it a lot for what if ... so whange /compare data a lot ..

So the quicker and easier to use ..the better 

Stephen

If all you need is to generate some scatterplots easily and with a GUI, have you tried gnumeric?  It can create charts pretty easily, and the statistical tools are second to none in the spreadsheet world.  You can also export your figures as svg.

---

### Post by roderikk on 2006-10-17
You could also look here: [https://help.ubuntu.com/community/UbuntuScientists](https://help.ubuntu.com/community/UbuntuScientists)

---

### Post by LaserJock on 2006-10-17
> **basilwatson said:**
> Ive downloaded gnuplot , but the command line looks daunting ..any with a GUI  ,,,
With Zgrapher for example I click Xy type in the info then click regression  /dy/dx and there is the result ... I have use it a lot for what if ... so whange /compare data a lot ..

So the quicker and easier to use ..the better 

Stephen

For a fair amount of stuff you can use this cool gnuplot frontend I packaged up called plotdrop. The homepage is: [http://icculus.org/~jcspray/plotdrop/](http://icculus.org/~jcspray/plotdrop/) if you want to see a little more about it. It's in the Universe repository.

-LaserJock

---

