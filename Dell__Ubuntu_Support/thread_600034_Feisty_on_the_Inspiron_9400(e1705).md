---
title: "Feisty on the Inspiron 9400(e1705)"
date: 2007-11-01
forum: Dell  Ubuntu Support
---

### Post by kidKazam on 2007-11-01
hi there,

i know many of are probably running gutsy at the moment, but i'm posting this in the hopes that someone finds this thread who had a similar problem to me. 

i'm trying to install feisty on my inspiron 9400. can't even get past initial installation because x won't start, so i'm positive it's something with my graphics card. i'm using the infamous ATI x1400, and after hours of googling i've yet to find a working solution. 

i've tried this line of code several times:

```
sudo apt-get install xorg-driver-fglrx 
```

which appears to work(says that some files were not found, ran --fix-missing). but then when i try 

```
sudo aticonfig --initial 
```

'aticonfig' cannot be found. this is the only solution i could find on the forums. worked for some people but not for me, am i doing something wrong?  my roommate has a gutsy cd lying around-should i just try my luck with 7.10?? gahh so frustrating, thanks for any help guys.

---

### Post by inyoka on 2007-11-02
This is relatively simple to solve, especially if you have knoppix.  basically Feisty Fawn has a problem configuring the xorg.conf for this system.  Once you have booted up you need to get to a terminal, try presseing 'CTRL'+'ALT'+'F1'.

First backup your xorg.conf file
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```
Then you need to edit /etc/X11.xorg.conf file with a command like:
```
sudo vim /etc/X11/xorg.conf 
```

Then press 'i' this takes vim (the text editor your using) into interactive mode, and scroll down until you get to the section that defines your resolution and refresh rates.  The settings I currently have are :
1440x900 60hz
I have attached my xorg.conf, but I am afraid its from Gutsy so be careful, and I can't remember exactly what I set, so check out the attachment for help.

If you have knoppix, boot into it because the xorg.conf is where I got the settings for my friends laptop (which I have just installed Gutsy on or I would have been able to be more helpful)

I have subscribed to this thread so any problems please ask.

FYI Gutsy installs without this problem on your laptop.

---

### Post by kidKazam on 2007-11-02
thank you so much inyoka, i'm gonna try that in a bit when i get home. only thing is i don't have knoppix, can i run those commands without it?

---

### Post by kidKazam on 2007-11-02
okay those commands didn't work.  i got to the xorg info terminal and i tried to match up the settings best i could but no luck -- X still won't load.

so after a while i figured i'd give gutsy a try. i put in the disk and restarted but it keeps loading up to the Feisty installation screen. Do i have to reset something or delete some files that Feisty wrote? At this point I think i'd like to start over and try my luck with Gusty.

---

### Post by inyoka on 2007-11-10
If the CD is in it should automatically boot to it.  You could try checking your BIOS to see if CD is before hard drive in the boot list.  

I don't like to mention this but I have a technician who used to work for me who had the same problem, and as it happened it he was booting up to the CD but couldn't tell the difference between that and booting normally, he saw an Ubuntu desktop and assumed he'd booted to the Hard Drive.

Sorry the reply took so long, for some reason I wasn't notified of your post.  Unfortunately I have finished installing Gutsy on my friends Inspiron laptop and don't have it with me to test anymore, but I'll try to help should you need it and I can call him if needed.

---

