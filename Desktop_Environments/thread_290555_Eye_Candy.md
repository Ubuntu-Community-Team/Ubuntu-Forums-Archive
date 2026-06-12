---
title: "Eye Candy"
date: 2006-11-01
forum: Desktop Environments
---

### Post by Al3xanR0 on 2006-11-01
I'm not a newb, I'm not a pro, I'm just a GNU/Linux user asking some questions about desktop effects. Now that we have dispenced with the formalities here is what I could use some assistance with. I recently purchased a Dell E1505 Dual Core Notebook.

Here are the specs that I beleive are the most pertainent:

Proc= T2700 2.16GHz/667MHz
LCD= 15.4 SXGA TL
Grfx= 256MB Nvidia GeForce Go 7300 TubroCache
Hdd= 120GB SATA
Mem= 512MBx2 Shared Dual Channel DDR2
Aud= Integrated Soundblaster Audigy
OPT=Double Layer DVD+/-RW

I loaded Kubuntu of course, tweaked it, backed up eveything, then decided it was time to add some eye-candy.  I came across this [Beryl-AiGLX Install How-to]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX") and got as far as 

```
sudo apt-get install xserver-xorg-air-core linux-dri-modules-common linux-dri-modules-`uname -r`

``` and discovered that the modules for my running kernel, "2.6.15-27-686" are not available. In fact a quick ```
apt-cache search linux-dri-modules
``` reveals the following available modules:


linux-dri-modules-2.6.15-22-386
linux-dri-modules-2.6.15-22-686
linux-dri-modules-2.6.15-22-k7
linux-dri-modules-2.6.15-23-368
linux-dri-modules-2.6.15-23-686
linux-dri-modules-2.6.15-23-k7
linux-dri-modules-2.6.15-25-386
linux-dri-modules-2.6.15-25-686
linux-dri-modules-2.6.15-25-k7
linux-dri-modules-2.6.15-26-386
linux-dri-modules-2.6.15-26-686
linux-dri-modules-2.6.15-26-k7
linux-dri-modules-common

Where can I locate the correct linux-dri-modules if none of these are viable? I noticed in my readingings that the use of DRI is usually synonymous wit ATI cards, does it matter that I have an "NV" card?  If it is not possible to install AIGLX, I would like to install XGL alternatively, where can I locate KDEcentric XGL/AIGLX/Beryl Install instuctions for my Kubuntu lappy?

Thanks in advanced for your help

---

### Post by lonce on 2006-11-01
If your running beryl with AIGLX you wont use DRI.  It has built in GLX support.

---

### Post by lonce on 2006-11-01
If you just type Beryl into the search box.  It will list a thread that is how to install beryl with AIGLX without XGL.  Thats what worked for me.

---

### Post by Al3xanR0 on 2006-11-01
> **lonce said:**
> If you just type Beryl into the search box.  It will list a thread that is how to install beryl with AIGLX without XGL.  Thats what worked for me.

Thanks Lonce, but search results yield instructions on how to install AIGLX/Beryl on EDGY I'm running Dapper which, is fine if the packages are not release specific. Is it possible for you to post a link to what worked for you?

Thanks again

---

### Post by lonce on 2006-11-01
If your on dapper there is also a post for how to install XGL and beryl on dapper.  Just look down the results for Beryl.  I am at work and dont have time to search for it.  If you cant find it I will search later.  Drop me an email if you cant find it and I will find it.

---

### Post by raqball on 2006-11-01
Does this help?

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL)

---

### Post by Al3xanR0 on 2006-11-01
> **raqball said:**
> Does this help?

[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/XGL)

Tried this and KDM failes to load, had to use the Kubuntu liveCD to restore my old xorg.conf. Really all I need is linux-dri-modules-2.6.15-27-686 because it is the only suitable match for my running kernel, but I can't seem to locate it. Thanks

---

### Post by compmodder26 on 2006-11-01
Before I upgraded to Edgy I was running Beryl on Dapper with the 2.6.17-686 kernel and I didn't need the dri modules.  Have you simply tried it without them?

---

### Post by Al3xanR0 on 2006-11-02
> **compmodder26 said:**
> Before I upgraded to Edgy I was running Beryl on Dapper with the 2.6.17-686 kernel and I didn't need the dri modules.  Have you simply tried it without them?

You know I thought to myself what the heck?! What have I to lose? so I decided to have a go at it. I knew that it would not work (generally speaking, any time there is a deviation of  protocol, subsequent catastrophe ensues) but, I was not going to allow that to hinder me. As afore stated, I attempted to install AiGLX and Beryl per [these instuctions]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX") with the exception of ```
sudo apt-get install linux-dri-modules-`uname -r`

``` and ```
sudo ln -s /usr/lib/xorg/modules/drivers/ /usr/lib/xorg-air/modules/
sudo ln -s /usr/lib/xorg/modules/input/ /usr/lib/xorg-air/modules/

``` of course, due to unavailabilty of the "linux-dri-modules-2.6.15-27-686" package for my running kernel as mentioned in previous post.

Upon the completion of the uneventful attempt I was left with a system that would hang at usplash after services load, oh how I longed for kdm to appear. Not to worry I used a trusty Mepis 6.0 cd I had lying around to mount my /etc/X11/ to restore xorg.conf from backup. Oh wait there's more! I was finally able to get a KDE session going which was when I discovered the Beryl had actully installed successfully and was running (with absence of AiGLX of course), however, with out window borders and the ability to type anything, anywhere. I ended the KDE session, booted into a console session removed all that I had installed finally restoring my system to square one. Thank you all for you help I'll be signing off now.

Regards
Al3xanr0

---

### Post by herson on 2006-11-10
Somebody knows when will be released linux-dri-modules-2.6.15-27-686?

---

### Post by serion on 2006-12-07
> **herson said:**
> Somebody knows when will be released linux-dri-modules-2.6.15-27-686?

BUMP


Anyone?  I'm running into the same problem.

---

### Post by Sn2 on 2006-12-16
i found here
deb [http://gandalfn.club.fr/ubuntu](http://gandalfn.club.fr/ubuntu) dapper .
do not forget the last dot
good luck;)

---

