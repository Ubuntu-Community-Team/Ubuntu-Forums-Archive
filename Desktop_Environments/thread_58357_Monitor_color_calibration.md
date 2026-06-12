---
title: "Monitor color calibration?"
date: 2005-08-19
forum: Desktop Environments
---

### Post by factotum218 on 2005-08-19
Anyone know where to start in regards to reaching proper color calibration on a Ubuntu system? All of the previous work I have done with photoshop looks a bit off and I need to get the color settings back where they are supposed to be so I can get my pantone colors to match up.

Thanks in advance

---

### Post by everything on 2005-08-24
I don't know of any professional program to calibrate monitor colors in Linux, but maybe there is something. 
In the meanwhile try using [FONT=Fixedsys]xgamma[/FONT] at the gnome terminal. This way you can pass the blue, the green and the red gamma percents to the X server, f.i. this way:

[FONT=Fixedsys]xgamma -bgamma 1.200 -ggamma 1.400 -rgamma 1.500[/FONT]

(of course you have to try different values).

When you are satisfied add the values to your xorg.conf file (I don't remember where. Make a little search, or try [FONT=Fixedsys]man xgamma[/FONT]) or add the command to your [FONT=Fixedsys].xinitrc[/FONT] file.

I hope I've been useful.
Bye.

---

### Post by jcornuz on 2006-03-02
Hi,

I have been using Ubuntu for photographic work for a while and screen calibration is doable, but you need a bit of work.

First, you need a icc (or icm) profile for your screen. I get it by booting on windows and using a colorplus calibration device to build it. 

Then there is a program called xcalib that allows you to load the newly created profile to your screen (basically it allows you to tweak your gamma more finely than xgamma by using the vcgt tags of the profile).

Finally you need to tell your photographic tool to use that same profile (Cinepaint does a good job with that, but gimp is still not quite there yet). 

And your all set :) 

Take care.

Joel

PS: This is just the basic idea. Let me know if you want more details.

---

### Post by imopen on 2006-04-02
Hi jcornuz, 
your post is very interesting, i have problems to calibrate my laptop lcd to work with photos. 

Which colorvision spyder do you own? 

Thank you in advance ;)

---

### Post by jcornuz on 2006-05-16
Hello I'm open :)

Sorry I only see your post now... I own the basic spider 1 kit from [http://www.colorvision.com]("http://www.colorvision.com") which was the first affordable kit, at the time.

Here are a few comments:

1) It is not very accurate to profile a monitor under windows and use the profile under Linux. But there is no way to run colorvision soft under Linux so we are stuck with it. Good enough but not ideal.

2) A laptop is not too ideal either to do photographic work. It used to be that CRT screens were the only ones good enough, also it looks like new LCD start to fit the bill, too. Anyway, a calibrated laptop screen will still be better than a non-calibrated one.8) 

3) If you want to print your photos, having a calibrated screen is only part of the setup. You also need to have a profile for your printer / paper / ink - and a program that knows how to handle all of it under linux. [http://cinepaint.org]("http://cinepaint.org") is the only one that I know of which is GPL.

Take care,

Joël

____________________________

[jcornuz.awardspace.com]("http://jcornuz.awardspace.com")

---

### Post by imopen on 2006-05-24
Thank you again, your post is very precious. In the meanwhile i bought Colorvision ColorPlus and i calibrated my notebook monitor under linux using windows profile as you told. It's not perfect but it's better than nothing ;) 

To print, at the moment, i use the printer only booting under windows (i have a Canon Pixma 5200)... i believe that print with same accuracy under linux is just a dream :-?

---

