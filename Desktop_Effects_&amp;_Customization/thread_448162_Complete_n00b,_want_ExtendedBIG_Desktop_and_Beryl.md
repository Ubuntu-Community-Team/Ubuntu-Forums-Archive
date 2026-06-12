---
title: "Complete n00b, want Extended/BIG Desktop and Beryl"
date: 2007-05-18
forum: Desktop Effects &amp; Customization
---

### Post by soccerdude21490 on 2007-05-18
Hey everyone, well the 2 things I want out of Linux is Extended Desktop (or as I see it being called "Big Desktop") as well as Beryl... if I had to give anything up, I would give up Extend Desktop

I have a 22'' Wide screen (primary, running right now at 1680x1050) and a 17'' normal screen(trying to get it to be on Extended Desktop and be at 1080x1024). with an ATI X1600 AGP Video card.

right now I have the "fglrx" installed because of trying to get Extended Desktop to work


but does anyone have any ideas (heard about XGL and AIGLX and what not?) I know these are probably stupid questions, but I'm trying to switch to Linux, and I searched around on teh forums some and haven't found anything THAT helpful  :)

---

### Post by WaeV on 2007-05-18
I don't know about the extended desktop, but this is a good site for setting up beryl on an ati machine with feisty:
[URL="http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon"]
http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon[/URL]


[Edit]
Actually I just checked your video card against the supported cards.  Completely supported is supposed to be the only ones that work, but I got beryl to work on my "experimental" card.  Unfortunately for you, your card is in the completely unsupported section, meaning you probably won't be able to use fgl and aiglx.

---

### Post by soccerdude21490 on 2007-05-19
hmmm I got beryl and fglrx and what not to seem to install, but I think I have too much installed now so Ubuntu is confused on which to use.


so what shou I exactly install to get Beryl working? I checked on their forums and some people are saying that the x1600 works

---

### Post by eks on 2007-05-19
> **soccerdude21490 said:**
> but does anyone have any ideas (heard about XGL and AIGLX and what not?) I know these are probably stupid questions, but I'm trying to switch to Linux, and I searched around on teh forums some and haven't found anything THAT helpful  :)

SoccerDude, I have the same configuration and goals (Radeon X1600, dual monitors and beryl) and I can advice you, you are in for a painfull ride... But that's due to ATI lack of support for Linux and OSS, not Ubuntu. So, as me, you need to have some patience on making beryl work on this hardware. I've wasted some 2 full days already without success, but learned a lot during this time.

Like, AIGLX won't work with this board, so you need XGL. For that you need fglrx drivers, the best is to get from the repositories (you can use Synaptic Package Manager). After you have the drivers working, you need xserver-xgl. Then make it run. Then beryl. 

You can follow [this thread]("http://ubuntuforums.org/showthread.php?t=440962&page=7"). And some other links:

[A very good tutorial]("http://lhansen.blogspot.com/2006/10/3d-desktop-beryl-and-xgl-on-ubuntu-edgy.html")
[Composite Manager info on help Ubuntu]("https://help.ubuntu.com/community/CompositeManager")

And when you make it work don't forget to tell me how!!! :D

Btw, the dual desktop is easy, worry about it later. To set it up you just need to add some stuff on the xorg.conf or use aticonfig. More on [here]("http://ubuntuforums.org/showthread.php?t=221174").

eks

---

### Post by soccerdude21490 on 2007-05-19
hey thanks, well Beryl seems to install find following the posts you gave me. But just some stuff liike creating,maximizing, etc are EXTEREMLY slow, which sucks for being such a powerful videocard (upgraded from 9600.. and that ran smoothly)

Still I'm not sure how I can make a Big Desktop or w/e using 1 monitor at 1680x1050 and 1 at 1080x1024... I've read people on the forums making it, but I haven't found code to put in a file (since I'm not exactly sure right now with windows, its hard for me to just mess with it)

---

### Post by eks on 2007-05-19
Forget about it, trash your ATI (or sell it) and buy a nVidia.

ATI drivers won't run Xgl on dual monitors setup. [Linky.]("http://ubuntuforums.org/showpost.php?p=2644217&postcount=131")

You can run Xgl and Beryl on one monitor. With a lot of pain, tho, the beryl-xgl was taken out of the repositories and 2.1 version of Beryl will not work with ATI, only 2.0.


eks

---

### Post by soccerdude21490 on 2007-05-19
ok haha, well what would be a good option to get for nvidia? I have an ATI X1650 512MB AGP card, so what about this, [http://www.newegg.com/Product/Product.aspx?Item=N82E16814143069](http://www.newegg.com/Product/Product.aspx?Item=N82E16814143069)  BFG Tech GeForce 7600GS 512MB... looks to be just as good (I'm guessing I would get basictly the exact performance out of both, or is one better?)

---

