---
title: "Beryl freezes my PC on Feisty"
date: 2007-06-11
forum: Desktop Effects &amp; Customization
---

### Post by laramarvin on 2007-06-11
Hi, I'll try to do as descriptive as possible:

   1. Problem: Beryl freezes my PC
   2. When: After a little while running Beryl or when changing beryl settings
   3. OS: Feisty Fawn Ubuntu 7.04 x86
   4. Graphics: 3D enabled with NVIDIA 7300 GS, Nvidia driver from nvidia.com
   5. Beryl: Downloaded and installed from Synaptic


Please help! Want my PC running with Beryl

---

### Post by zero244 on 2007-06-11
The problem is most likely the drivers in relation to your video card. If your computer is freezing it will continue to freeze. Beryl either works or it doesn't work.
If it doesn't work I would forget it.......it will eventually break your OS and you will have to install all over again.
Getting the Nvidia drivers to work with some cards is so complicated and tricky only a expert can install them correctly. Beryl is and will always be a beta project that works for some but not for most.
You might try xcompmgr if your computer freezes fairly quickly with it that points to incompatible video drivers.

---

### Post by laramarvin on 2007-06-12
Should I try using an old version of Beryl? 0.2.0 maybe?

---

### Post by kmepartaunrayo on 2007-06-14
it used to work great for me in feisty!!! ..... but you know reading here and there i saw that i could install some SVN version that looked nice! so i decided to try it.... and... ehmm.. it didnt work... at least i couldnt make it work so i decided to reinstall the one i had... and when i run it it freezes!! .... so i have to go to ctrl alt f1 and uninstall it from there with sudo apt-get remove beryl ..... and i can log back in!  .... the first time i reinstalled beryl it worked but without the minimize, close.... bar up there..  and i started moving some settings on beryl manager and thats when it forze the first time... and from there on it freezes everytime i run it! :-s!! i tried reinstalling it but it didnt work.... can anyone help? :)??

---

### Post by laramarvin on 2007-06-14
Too much configuration for a newbie, have you tried reinstalling feisty all over again and them install beryl? That  may work since you said it worked for you at the beginning.

Mine still freezes it out, but I'll try this:

sudo apt-get install beryl beryl manager esmerald-themes **--fix-missing**

The new thing on that is that the --fix-missing will add any file it didn't load the first time. I hope this help for me. I'll let you know guys.

---

### Post by zero244 on 2007-06-15
Ok I finally got Beryl running pretty good on my Nvidia 7600 GS card.
I tried every combination driver available and beryl kept freezing me solid. I could move the mouse but thats it.
So I remembered I use to use XGL with my ATI card and set up my computer with XGL with my Nvidia card.
It has worked very well virtually all the features work and its pretty stable as well.
add the repositories to you sources.list for version 0.2.0 nothing higher because I think they removed the XGL server from later releases.
Add this to your sources list

gksu gedit /etc/apt/sources.list

# deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main
Then search synaptic for berly and you should be able to download the complete package.
Make sure its version 0.2.0 only.

---

### Post by laramarvin on 2007-06-25
Hey Zero, I'll try that asap. Sorry for the next question but, how did you enable XGL with the NVIDIA card?

---

### Post by zero244 on 2007-06-25
I cant seem to find the link where I installed from.
Look for a How to that shows you how to setup XGL in a separate session. 
You will have to create a couple of scripts..........nothing more than cut and pasting.
I will try to find the How To I used.
Beryl is working about 95 percent stable.
Im using it right now.
Also I am using the Automatix Nvidia Drivers.
Check out Automatix2 it has some easy click and run scripts for installing video codecs, ntfs support etc.

---

### Post by skalliett on 2007-08-05
Hi everyone, has anyone found a solution yet? I have the same problems but with an ATI card. The XGL seems to be running fine but as soon as I turn on beryl and move a window around or something it freezes...grateful for som help here

---

### Post by zero244 on 2007-08-06
I thought I would throw this in..........beryl, compiz and any other 3D desktop manager I tried would freeze me solid.
After two months or more of trying everything with nothing working. I found out the brand new nvidia card I bought was defective.
I sent the card back for exchange and have had no problems at all with Linux or beryl since.
So you might consider that possibility.....it may be a long shot, but it happened to me.
I did get a ATI card to work with beryl, it was a fairly common chipset card.
But I think the nvidia cards in general are less problematic.
Both of my machines have nvidia cards and I havent had any issues with either one running beryl.
Good luck.

---

