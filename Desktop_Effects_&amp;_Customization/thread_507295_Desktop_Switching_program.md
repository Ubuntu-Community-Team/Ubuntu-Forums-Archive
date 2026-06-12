---
title: "Desktop Switching program"
date: 2007-07-22
forum: Desktop Effects &amp; Customization
---

### Post by BDNiner on 2007-07-22
Is there a program that would allow me to change my desktop picture randomly. Like every time a log in, or after a predefined interval?

---

### Post by bbzbryce on 2007-07-22
Here's a simple script which does this. I forgot where I originally found it so I can't give credit to the person who wrote it.

```
#!/bin/bash
WALLPAPERS="/home/bryce/Pictures/backgrounds-1680x1050" #change this path for your system
ALIST=( `ls -w1 $WALLPAPERS` )
RANGE=${#ALIST[@]}
let "number = $RANDOM"
let LASTNUM="`cat $WALLPAPERS/.last` + $number"
let "number = $LASTNUM % $RANGE"
echo $number > $WALLPAPERS/.last
gconftool-2 -t string -s /desktop/gnome/background/picture_filename $WALLPAPERS/${ALIST[$number]}
```

Change the path and save it to a file, then chmod +x the file so that it can be executed. Then run it when you want it to change. I setup a cron job to switch my wallpaper every hour.

---

### Post by BDNiner on 2007-07-22
That is great, now how about a different picture on each of the desktops?

---

### Post by bbzbryce on 2007-07-22
> **BDNiner said:**
> That is great, now how about a different picture on each of the desktops?

I'm not sure how to accomplish that. Perhaps someone has written a package to handle it.

---

### Post by BDNiner on 2007-07-22
> **bbzbryce said:**
> Change the path and save it to a file, then chmod +x the file so that it can be executed. Then run it when you want it to change. I setup a cron job to switch my wallpaper every hour.

What is cron and how do i set it up to change my desktop every hour?

Sorry for being a newbie.

---

### Post by bbzbryce on 2007-07-22
> **BDNiner said:**
> What is cron and how do i set it up to change my desktop every hour?

[Cron]("http://en.wikipedia.org/wiki/Cron")


To configure type:
crontab -e

Then paste this in:

```
  0 *  *   *   *     ~/switchWallpaper
```

This will then execute switchWallpaper at the 0 minute of every (the star) hour, day of month, month, and day of week.

---

### Post by HermanAB on 2007-07-22
KDE can do all of that, so maybe next time install Kubuntu.

Cheers,

Herman

---

### Post by bbzbryce on 2007-07-22
> **HermanAB said:**
> KDE can do all of that, so maybe next time install Kubuntu.

This isn't very relevant to this thread, but KDE can be installed from the repository package kubuntu-desktop. On login one can then select which to run.

---

### Post by BDNiner on 2007-07-22
I am not a huge fan of KDE, i use it on the SLED 10 computer at work. It reminds me too much of windows. But i am customizing that computer also. Gnome is simpler, but some of KDE's apps are more useful. Tough decision, but on look and feel alone, i like the simpler gnome so far.

---

### Post by steveneddy on 2007-07-22
um - try searching google for wallpapoz

---

### Post by BDNiner on 2007-07-22
Thanks for the link. i am going to install this immediately and see how it goes.

---

### Post by kyalee on 2007-09-19
Sorry to resurrect such an old thread, but I had a few questions.

One, when you save the script, what type of file extension should it have. (I'm a totally newbie, I know. :/)

Second, I assume setting up the chron is done in the terminal, but I wanted to double check. Is that right?

---

### Post by bbzbryce on 2007-09-19
> **kyalee said:**
> One, when you save the script, what type of file extension should it have. (I'm a totally newbie, I know. :/)

The script doesn't need any extension, however since it is a bash script I sometimes use the extension **.sh**.

> **kyalee said:**
> Second, I assume setting up the chron is done in the terminal, but I wanted to double check. Is that right?

Correct you run crontab -e from the command prompt.

---

### Post by kyalee on 2007-09-19
Woo-hoo, I got it working. Thanks so much! :D

---

