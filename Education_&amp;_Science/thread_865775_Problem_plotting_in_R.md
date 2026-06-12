---
title: "Problem plotting in R"
date: 2008-07-21
forum: Education &amp; Science
---

### Post by gvanto on 2008-07-21
Hi, I have a file in the following format:

date, open,high,low,close,vol
2008-7-21 9:50:0,        -1,     -1,     -1,4930.000,1
2008-7-21 9:50:1,        -1,     -1,     -1,4930.000,4
2008-7-21 9:50:2,        -1,     -1,     -1,4931.000,1
etc...

which I read in as follows:

```
secdata = scan("apu8_2008-7-21.csv", list(dt="", open=0, high=0, low=0, close=0, vol=0), sep=",", skip=1)
```

this works fine. What I would like to do is plot the close series, with respect to the first column. So far, I've only managed to plot the close series itself:

```
plot(secdata$close, type="l")
```

when I try to do
plot(secdata$dt, secdata$close, type="l") - a blank graph comes up. I'm guessing I need to convert the secdata$dt to some kind of 'date' object - does this exist in R?

Any help would be much appreciated!

Gerry
R-newbie

---

### Post by NikoC on 2008-07-21
Hmmmz, what if you do:

secdata<-read.csv(file="apu8_2008-7-21.csv",header=T,sep=",")
attach(secdata)
plot(date,close,type="l")

Keep us updated!

Cheers.

---

### Post by Tart on 2008-07-21
> **gvanto said:**
> 

I'm guessing I need to convert the secdata$dt to some kind of 'date' object - does this exist in R?

Any help would be much appreciated!

Gerry
R-newbie

Hi 
I think you are correct about "date" formats. I really hate giving answers like this, but I never worked with time stamps before. Check

>?as.Date  
>?as.POSIXct

I know this two function work with various date/time formats.
First one is for dates without times. Second one has dates and times, including time zones. 

I hope this is what you are looking for.

Good luck

---

### Post by fsando on 2008-07-21
Hi gvanto
As far I can see you should convert secdata to a data.frame:
```
secdf <- as.data.frame(secdata)
plot(secdf$dt,secdf$close)
```

---

### Post by gvanto on 2008-07-22
fsando and NikoC - thanks alot you guys' solutions seem to be on the right track.

They both seem to do the same though: which is plotting the points but extremely slowly - the date legend on the x-axis is also horizontal and i think needs to be vertical so it can fit in...?

I've attached the file if anyone would like to see if they can plot this a bit more efficiently than I am! :-)

help much appreciated again on this

thanks
gerry

---

### Post by NikoC on 2008-07-22
secdata<-read.csv(file="apu8_2008-7-21.csv",header=T,sep=",")
x<-strptime(secdata$date,"%Y-%m-%d %H:%M:%S")
plot(x,secdata$close,type="l",xaxt="n")

You just have to fiddle around with the x-axis labels, but I'm sure you can figure that out, google is your friend :lolflag:

---

### Post by fsando on 2008-07-22
Now I've been researching this a bit further - and solved it.

I can say that you've hit a nasty one.

This will do the trick
```
dat <- read.csv('apu8_2008-7-22.csv')
plot(as.POSIXlt(dat$date),dat$close,type='l')
```

The as.POSIXlt() is how you get a usable date format for your situation. There are quite a few different (very different) ways of converting into dates.

> **NikoC said:**
> 
You just have to fiddle around with the x-axis labels, but I'm sure you can figure that out, google is your friend :lolflag:
have a look at ?par to get all the goodies on plotting

And... I completely forgot: You MUST check out rkward the beautiful interface to R

---

### Post by gvanto on 2008-07-29
thanks a million for your help on this!

fsando your code is great :-)

par(ls=2) does the trick nicely for x-axis tick labels.

The only problem I have remaining on this issue is that:
currently the dt values are being displayed in ACTUAL order, rather
than in the order that they are being read - any idea if its possible to just display this in read-order?

you guys are champions, I'm loving R more and more!

---

### Post by fsando on 2008-08-01
> **gvanto said:**
> thanks a million for your help on this!

fsando your code is great :-)

par(ls=2) does the trick nicely for x-axis tick labels.

The only problem I have remaining on this issue is that:
currently the dt values are being displayed in ACTUAL order, rather
than in the order that they are being read - any idea if its possible to just display this in read-order?

you guys are champions, I'm loving R more and more!

I'm not sure I understand you completely.
If you want the 'close' variable plotted as the values appear and at the same time want the date variable as labels I get the feeling that your wish is not entirely meaningful (I'm probably wrong)

There could be a couple of ways to achieve that (I'm not sure the exact coding here)

You could create an index variable numbering the cases from 1 to nrow(dat) and use that as the x-axis
```
dat$newindex <- 1:nrow(dat)
```
And then either assign the dates as labels to that variable - you'll want to look at the 'levels' command or the 'factor' command, perhaps a related command.
Or it should be possible to assign the date variable as labels directly to the plot command. This is, as I recall, a bit complicated but doable.

I don't have R installed on this machine so I have to improvise from memory.

Hope that helps.
Good Luck

I'd recommend
[Rkward]("http://rkward.sourceforge.net/index.php?content=home")

EDIT (2008-08-02):
Just re-read your post and I think I got it wrong:
It's a bit complicated. You want to sort the data.frame according to date, there should be a command for sorting a whole data.frame but I don't remember it right now.
Another way is to first sort the date variable, get a reference between the old and the new sort order and use this reference to reorder the 'close' variable in the same order. This can be done like this:

```

#read the data file
dat <- read.csv('apu8_2008-7-22.csv')
# create real dates from character variable
date <- as.POSIXlt(dat$date)
# sort dates and return reference between old and new sort order
sorted_date <- sort(date,index.return=TRUE)
# rearrange 'close' in same order as 'sorted_date'
sorted_close <- dat$close[sorted_date$ix]
# do the plot
plot(sorted_date$x,sorted_close,type='l')
```
This code should do the trick if I understood you correctly. I haven't tested it, though, as it's done from memory.

---

### Post by gvanto on 2008-08-03
Hey Fsando,

Thanks again for your help.

Currently the plotter sorts the plot by date, (which is a very reasonable assumption to make).

I was actually meaning to plot the date (and their values) in order of being read in, so that if a later date is read in first, it;s still plotted first.

But this really is not a issue for me, and in fact I think the default plotting of date-order is better and enforces correctness

thanks for the RKward link - this application looks awesome!

What's your background fsando  - are you in trading too?

Best
G

---

### Post by gvanto on 2008-08-07
Hey,

Does anyone know if there's a way to enter the tab format
using sprintf: I get the following which is no good :-(

```

print(sprintf("hello \t world"))
[1] "hello \t world"

```

Help appreciated!
Gerry
R-newbie

---

### Post by machoo02 on 2008-08-07
Have you tried using cat()?

```
> cat(sprintf("hello \t world\n"))
hello 	 world
> cat("hello\tworld\n")
hello	world
> 
```

---

### Post by gvanto on 2008-08-07
awesome thanks a million!

---

### Post by gvanto on 2008-08-08
Hey does anyone know how to enable autocomplete in the R-script 
code editor in Rkward?

This would be so handy,especially for long variable names!

help much appreciated
Gerry

---

### Post by gvanto on 2008-08-08
Ok I have found the word completion plugin (KTextEditor word completion plugin).

The main problem when using it now is that when I am indented (the cursor is at indented position, e.g. within if() statement), and word completion comes up, i press enter to select the variable which it does BUT it puts it at the very start of the line!

```


if( chg_Cp_C > 0 && chg_C_Ot > 0) { 
	same_dir_list <- c(same_dir_list, 1);
	#here i start typing sam... word complete comes up
	but when I select it, here's what happens:
same_dir_list #it goes here! :-(
				
}


```

Is it perhaps that I shouldn't use the ENTER key to select the word in the auto-popup word completion?

help much appreciated!
Gerry

---

### Post by fsando on 2008-08-10
> **gvanto said:**
> Ok I have found the word completion plugin (KTextEditor word completion plugin).

The main problem when using it now is that when I am indented (the cursor is at indented position, e.g. within if() statement), and word completion comes up, i press enter to select the variable which it does BUT it puts it at the very start of the line!

```


if( chg_Cp_C > 0 && chg_C_Ot > 0) { 
	same_dir_list <- c(same_dir_list, 1);
	#here i start typing sam... word complete comes up
	but when I select it, here's what happens:
same_dir_list #it goes here! :-(
				
}


```

Is it perhaps that I shouldn't use the ENTER key to select the word in the auto-popup word completion?

help much appreciated!
Gerry

Hi
I was about to answer you question earlier. Auto completion was removed around the beginning of the year (with version 0.5 as I recall). It simply was the single most annoying feature, it did for some reason not work as intended. It blocked your typing and sometimes even had you losing your work by accident.

---

### Post by gvanto on 2008-08-10
Oh no! :-(

An Auto-Complete feature is so handy (I use it in Eclipse for Java coding ALOT).

Thats a real shame its not in RkWard - any plans for it to come in?
(It'll make rkward even more awesome than it already is!)

cheers
Gerry

---

### Post by fsando on 2008-08-11
> **gvanto said:**
> Oh no! :-(

An Auto-Complete feature is so handy (I use it in Eclipse for Java coding ALOT).

Thats a real shame its not in RkWard - any plans for it to come in?
(It'll make rkward even more awesome than it already is!)

cheers
Gerry

Yes me too use it in eclipse and even in OpenOffice ;).

I believe the editor is embedded Kate (or another KDE editor) so it is probably not really RKWard that provides it, though I'm not sure how those things work.

---

