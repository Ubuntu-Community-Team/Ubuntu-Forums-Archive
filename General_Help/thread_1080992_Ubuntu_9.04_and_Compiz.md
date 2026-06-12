---
title: "Ubuntu 9.04 and Compiz"
date: 2009-02-26
forum: General Help
---

### Post by ThePablo69 on 2009-02-26
I upgraded from Ubuntu 8.10 (which ran compiz smoothly with my crappy Intel graphics card) to 9.04 (Alpha 4), and now Compiz lags a lot, the cube effect is really slow, and the window decorations dont appear at times. Is anybody having this problem? Or does anybody know how to fix this?

---

### Post by jackabus on 2009-04-23
Yea I have the same problem the cube just seems slower than it did with 8.10. It sucks cause I use that option often.

---

### Post by LT1Caprice57L on 2009-04-23
My cube and shift switcher work great, but everything else is slower than molasses.

Dell Inspiron 600M, Pentium M @ 1.7 GHz, 1GB RAM, ATI Mobility Radeon 9000.

Everything ran smoother than a baby's back on 8.10.

Additionally, turning Compiz off resulted in windows rendering slowly, not snappy like in 8.10.

EDIT: Looks like I'm one of the unlucky ones with a graphics adapter which ATI dropped support for.  That would explain it.

---

### Post by Eneerge on 2009-04-24
I, also, have noticed a lot more lag with Compiz in 9.10 with restoring windows than I did with 8.04/8.10.

The cube and most animations work just fine, but the problem is restoring windows after they've been minimized.  I see about 2-2.5 seconds delay before the window even tries to display.  Occasionally after the delay, the zoom-up animation plays to bring it up.  Usually, though, the animation never even occurs and the window just appears.  2.5 seconds is a long time for changing windows on any system especially when your trying to get some work done.

Worthy Specs:
Intel C2D E6700 @ 3.2ghz
ATI Radeon HD4840
4gb RAM

---

### Post by MediocreHippie on 2009-04-26
i noticed the same thing on my Toshiba Satellite L305. 
mainly just the compiz cube. it has really bad lag. will they fix this?

---

### Post by chezzo on 2009-04-27
me too! :(
also, graphics-heavy apps like awn and boxee are a lot slower

---

### Post by anarkae on 2009-04-28
I have the same problem with my Acer Aspire 5610z
1.6 GHz Intel Core Duo processor, 
2 GB DDR2 memory
Intel GMA 950 integrated graphics. 

I was very happy with 8.10! :(

Please heeeelllp!!!

---

### Post by networm1230 on 2009-04-28
hello. I have compiz installed on my pc what is your problem with comipiz?

installing?, configring?, I have some experience with it maybe I can help

---

### Post by boogers on 2009-04-28
You might want to try rolling back your drivers.
Here check out this page...[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

---

### Post by networm1230 on 2009-04-28
yes, Compiz is prosesor hungry and graphicly hungry useing Compiz will replase you ubuntu interface. but you can still force it to use you prafrance. to change to your visule interface and change it mid livel doing this will not use as much cpu and gpu power

good luck

---

### Post by networm1230 on 2009-04-28
> **boogers said:**
> You might want to try rolling back your drivers.
Here check out this page...[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

yes, go back on the drivers this can help. vary good advice. (boogers) I like your name cool dude

---

### Post by anarkae on 2009-04-29
> **boogers said:**
> You might want to try rolling back your drivers.
Here check out this page...[https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4](https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4)

Thanks boogers!
It works for me!!!
I'm very happy!!!

:guitar:

---

### Post by medic0079 on 2009-05-04
ok new and dumb... how do I do this...
Add the following lines to your /etc/apt/sources.list:

 deb [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main
 deb-src [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main

I tried entering /etc/apt/sources.list into terminal, and it said permission denied, I tried adding  deb [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main
 deb-src [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main
to the third party softwear sources list under admin/software sources
no luck
thanks for the help

---

### Post by sacredeagle on 2009-05-05
> **medic0079 said:**
> ok new and dumb... how do I do this...
Add the following lines to your /etc/apt/sources.list:

 deb [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main
 deb-src [http://ppa.launchpad.net/siretart/ppa/ubuntu](http://ppa.launchpad.net/siretart/ppa/ubuntu) jaunty main


Open a terminal and do:

**sudo gedit /etc/apt/sources.list**

paste the two lines into the file, save and close. in the terminal:

**sudo apt-get update**

then the changes are there.

---

### Post by johnswb on 2009-05-10
I've read this forum and other and still yet to see how to even get Compiz running.  I go to the package manager and I can see that it is already installed but done have a queue how to get it started.  When I run it from a terminal I get the following.
```

:~$ compiz
Checking for Xgl: not present. 
xset q doesn't reveal the location of the log file. Using fallback /var/log/Xorg.0.log 
Detected PCI ID for VGA: 
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Checking screen 1Comparing resolution (1400x1050) to maximum 3D texture size (4096): Passed.
Checking for Software Rasterizer: Not present. 
Checking for nVidia: not present. 
Checking for FBConfig: present. 
running under gnome seesion, checking for gnomecompat
Checking for Xgl: not present. 
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
```

I then installed the CompizConfig setting manger... and now it works...but with a few problems with everything not working like the cube.

---

### Post by devosion on 2009-05-12
Im having the same problem on my pc with nvidia drivers. First my compiz-settings-manager disappeared from my system menu, and then when I tried running it from terminal I got the exact same message. Strangely enough compiz was working perfectly a few days ago. Im guessing its an update I havent had a chance to check on yet that broke it. But help is also useful. :)

---

### Post by MScapee on 2009-07-24
For those of you who just want to see Compiz run on your desktop in some way, shape or form (and run smoothly at that) without fear of hosing your ubuntu install, I highly recommend downloading, burning and booting from the Linux Mint live CD version 7 (Gloria).  You can download it here: [http://www.linuxmint.com/download.php](http://www.linuxmint.com/download.php).  Compiz is installed on the live CD already.  All you have to do is boot the CD and enable Compiz from the menu -- it's that easy.  

I'm running a 2003/2004 vintage Gigabyte GA-7VT600 with 1G memory, 1.8ghz AMD Athlon (Barton) with an ATI 9000 (rv-250) graphics card and surprisingly, everything runs fast and smooth as silk.  Given how "ancient" and modest my hardware is (and having noted that there seemed to be some doubt as to whether this particular graphics card will work with Compiz at all), I have to say I'm blown away by the performance!  I thought for sure with my set up that Compiz would be dragging if it ran at all.  Nope!  It phucking kicks man!!!!!!! \\:D/  Now if I could only get this to work on my ubuntu 9.04 install, I'd be set!

---

### Post by prabath_fun on 2009-09-24
Hi,
   I am facing the problem that, Whenever I press super+tab keys, PC gets logout. Any help or fix for this????

---

### Post by prabath_fun on 2009-09-29
Please update me, How to set the thumbnail veiw for active windows when mouse pointer moved over the task bar icons.
Prabath

---

### Post by prabath_fun on 2009-10-04
I got thumbnail preview by enabling the "windows preview" in "Extras" plugin in "compizconfig settings manager".
Prabath

---

