---
title: "strange video effects in KDE and Firefox using Flash"
date: 2011-04-19
forum: Desktop Environments
---

### Post by linuxone on 2011-04-19
Hi,

since some time I notice a real disturbing video effect:

I use Firefox 4 and Adobe Flash 10 (current version). When opening a web page which contains a flash video this video keeps part of the screen on both (!) desktops. (see attached pictures)

Closing or minimizing all programs the video window is invisible. The video window will appear each time a program - any program! - window does appear above the area where this video windows is placed. I open Kate or OpenOffice or any other program and video window will appear again - see pic #1.

No matter if the video was started or not, the effect does happen everytime.
No matter if the FF tab or the entire browser was closed or not, the effect will stay until X-Server restart.

Even if I switch to the second desktop, the effect will appear. For example I launched Virtualbox on the 2nd desktop, open a Win XP system - the entire desktop background is blue. I opened Chrome and the video window from desktop #1 appears within the Chrome window. (see pic 2)

The effect will not appear into screendumps, so I used my smartphone cam for both pictures:

#1: after opening [www.tagesschau.de](www.tagesschau.de) I closed firefox and re-opened FF with another web page. You can see the video screen from tagessschau.de within the heise.de page.

#2: then I switched to desktop #2, run WinXP into a Virtualbox window and launched Chrome.

Nvidia Gforce 9800 GTX+
current Nvidia driver from nvidia.com
Kubuntu 10.10 amd64 and KDE4
all updates installed

As I do remember this effect happens since Flash 10. Unfortunately it is nearly unimpossible to use Internet without an installed Adobe Flash 10. If it would be possible I would remove Flash immidiately from any computer - I really would prefer this solution!

Is there any solution to solve this video effect except killing flash on the entire web?

Thomas

---

### Post by oldos2er on 2011-04-19
Are you using 64-bit flash?

---

### Post by linuxone on 2011-04-19
Hi,

> **oldos2er said:**
> Are you using 64-bit flash?

no, still 32-bit. 64-bit is unstable and not really usable.

Th.

---

### Post by el_koraco on 2011-04-19
I've heard a lot of people with KDE having these problems lately. I think someone said Adobe put out a patch on it's website. On the other hand, I'm having all out X lockups when trying to watch flash videos full screen on Kubuntu Natty. 

Similar bugs: [764650]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/764650") and [746865]("https://bugs.launchpad.net/ubuntu/+source/flashplugin-nonfree/+bug/746865")

Although both of these are ATI related.

---

### Post by marl30 on 2011-04-19
I'm using the 64 bit flash in Kubuntu without any issue. I use to have some weired issues running the 32 bit flash on 64 bit in both Gnome and KDE.

---

### Post by SeijiSensei on 2011-04-19
> **linuxone said:**
> no, still 32-bit. 64-bit is unstable and not really usable.

That hasn't been my experience with the "[Square]("http://labs.adobe.com/technologies/flashplayer10/square/")" versions.

---

### Post by schnelle on 2011-04-19
> **el_koraco said:**
>  I'm having all out X lockups when trying to watch flash videos full screen on Kubuntu Natty. 


I had fullscreen lockups with fglrx and I solved it with disabling hardware acceleration in flash. Right click on flash video>settings> uncheck "enable hardware acceleration".

Cheers.

---

### Post by oldos2er on 2011-04-19
> **linuxone said:**
> Hi,



no, still 32-bit. 64-bit is unstable and not really usable.

Th.

I've had a much better experience with 64-bit flash than 32-.

---

### Post by el_koraco on 2011-04-20
> **schnelle said:**
> I had fullscreen lockups with fglrx and I solved it with disabling hardware acceleration in flash. Right click on flash video>settings> uncheck "enable hardware acceleration".

Cheers.


Nope, but I'm using the radeon driver, so it's not really comparable. Disabling hw acceleration on flash makes flash go into fullscreen, but exit it immediately. As for fglrx, with my card it's a nightmare. The system goes into killer mode the second it's activated. If I do purge it, either simply, aggressively, or with maximum brute force, I get a week's worth of work done before X goes down. 

lol, after my experiences with Ubuntu, i did try to enable it in Kubuntu, but as soon as I saw the system taking the same path i just reinstalled from scratch.

---

### Post by linuxone on 2011-04-20
Hi,

thanks for all answers.

> **SeijiSensei said:**
> That hasn't been my experience with the "[Square]("http://labs.adobe.com/technologies/flashplayer10/square/")" versions.

I tested this Flash 64-bit version once again and square release 3 seems to work. It needs some more tests, but checking a few video web pages the strange effect does not happen again.

Thomas

---

