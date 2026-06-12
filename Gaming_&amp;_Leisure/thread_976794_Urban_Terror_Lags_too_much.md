---
title: "Urban Terror Lags too much"
date: 2008-11-09
forum: Gaming &amp; Leisure
---

### Post by frank.zappa on 2008-11-09
I have an integrated Intel GMA 950 but when I play Urban Terror in Vista, it runs smoothly, and even at times of lag it won't go under 25fps with an average of 35fps.

But when I run it in Ubuntu or Debian (well now only Debian, I removed Ubuntu) I can't get anything over 25fps with an average of 15. 

I'm it's not a processor or RAM problem as I have an Intel Core 2 Duo 1.6GHz and 2GBs of RAM but I'm guessing it has to do with OpenGL. I'm not sure how to configure it so if someone has any solutions and could help me, it would be appreciated.

---

### Post by EdThaSlayer on 2008-11-09
Here are some questions you will have to answer if you want to get an answer(a quick one that is :) ):

1. What type of graphics card do you have? 
2. Have you installed the proper graphic card drivers?

or if you are sure your graphics card is either an Nvidia or ATI I recommend installing the necessary graphic drivers either through the restricted driver installation option that Ubuntu should have or through Envy, a very useful GUI application that will help you choose the drivers needed("sudo apt-get install envyng-gtk" in the terminal).

Hope it helps. :D

---

### Post by Mike'sHardLinux on 2008-11-09
> **EdThaSlayer said:**
> 

1. What type of graphics card do you have? 


I'd bet it's integrated Intel GMA 950 graphics. :)

---

### Post by Irritant on 2008-11-09
Integrated intel chipsets are horrible performers.  You could plunk down 30 or 40 dollars for a low end Nvidia card and double that framerate easily.

---

### Post by frank.zappa on 2008-11-09
First of all it's an integrated Intel GMA 950 with 256MB of shared RAM - and as I stated, I get very decent frame rates when playing the same game in Vista with DX9, but with OpenGL in Linux, it lags, with all of the graphics settings the same as in Vista.

Second, I can't upgrade (:() because I'm using a laptop (which is the reason I'm not playing CoD4 lol).

Third, I'm not using Ubuntu, I'm using Debian, and the graphics drivers were automatically installed for me. But even when I had Ubuntu (just got rid of it 2 days ago) I had the exact same performance - if not better now that I'm using Debian.

I'm thinking of installing Google Earth to see how OpenGL does in that, because after I had updated my Ubuntu to Intrepid, anything with graphics would appear as 'tv static'.

---

### Post by frank.zappa on 2008-11-15
Ok I was reading another thread and figured out what the problem was. I did the following:
```
$ sudo dpkg-reconfigure xserver-xorg
```
and answered all the questions. Most of them were about the keyboard layout but there was one about 'kernel framebuffer' if I remember correctly. In the description, it said enable it if in doubt, so I enabled it. When I tried playing UrbanTerror I got framerates equivelent to those in Vista and no "stuttering" playback.

I made a backup of my xorg.conf file and basically the only difference was:
```
Section "Device"
        Identifier      "Configured Video Device"
        **Option          "UseFBDev"              "true"**
```
Before I did the reconfigure, the bolded text wasn't there.

Just thought I'd post this incase someone else has the same problem.

---

### Post by Velophile on 2009-08-05
Thanks for posting that frank, I've got the same situation and will be interested to see if I get the same results when I test it later.

---

### Post by j-d33zy on 2009-09-22
i tried changing it, seemed faster in the beginning, but it quickly slowed down, i think this problem may be individual to my laptop however, it has an nvidia 570m and i think its using some kind of throttling on my gpu. any more tips would be awesome.

---

