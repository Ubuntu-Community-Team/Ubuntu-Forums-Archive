---
title: "Wow. I'm dumb. How do I change it back?"
date: 2008-12-07
forum: General Help
---

### Post by Poyzin on 2008-12-07
Okay. Well. I'm a new Ubuntu user and I had no idea I couldn't use the programs I could in windows. I NEED some of the windows only programs. Like Visual Basic 6, Ulead Video Studio, Fruity Loops, etc.

I did a full ubuntu take over. How would I get my vista back :P.

Sadly, compaq doesnt like to hand out the windows CDs when u buy a pc.

---

### Post by eBoxNet on 2008-12-07
You are able to run windows applications (not all) on ubuntu by using Wine,you can download it from here : 

[http://www.winehq.org/site/download](http://www.winehq.org/site/download)

if some win app wont run via wine you can find linux applications for ubuntu to do the same things you where doing on windows.

---

### Post by lisati on 2008-12-07
If you're in luck, there will be a recovery partition on your system (my Compaq desktop came with one), but that's unlikely if you told Ubuntu to use the whole disk.....

My first question is this: when you first power-up your computer, is there something like "Press F10 to start recovery" showing? If the recovery partition is still there, this should call up the recovery options.

An aside:  the best kind of recovery CD/DVD is the one which comes with your computer, or one you can make using the software that is preinstalled on your system to make one (could be difficult if you've wiped Windows). The next best one is one you get from the shop who sold you your machine. 

There are other options for obtaining Windows disks but I hesitate to mention specifics because of potential legal hassles (and occasional "surprises" in the form of malware)

EDIT: I forgot to mention "Wine" which will let you run SOME (but not all) Windows software (see previous post)

---

### Post by Slim Odds on 2008-12-07
> **Poyzin said:**
> Sadly, compaq doesnt like to hand out the windows CDs when u buy a pc.

I keep seeing people say things like this, but it's just not true.

They give you something called a "recovery CD", which contains the operating system and some applications, drivers, etc.

There may be additional discs with apps and/or drivers.

---

### Post by eBoxNet on 2008-12-07
They don't give recovery cds anymore they are just create a recovery partition.

My new HP had one.

---

### Post by eBoxNet on 2008-12-07
HP PCs that ship with Microsoft Windows XP and Compaq Presario Desktop PCs made in spring of 2003 and later already come with a hidden preloaded recovery partition. This hidden partition can be used to recover all of the original software in the event of a major problem by pressing the F10  key repeatedly when the computer is first started.

Link : [http://h10025.www1.hp.com/ewfrf/wc/fastFaqLiteDocument?lc=en&cc=uk&dlc=en&docname=bph08097](http://h10025.www1.hp.com/ewfrf/wc/fastFaqLiteDocument?lc=en&cc=uk&dlc=en&docname=bph08097)

---

### Post by lisati on 2008-12-07
> **Slim Odds said:**
> I keep seeing people say things like this, but it's just not true.

They give you something called a "recovery CD", which contains the operating system and some applications, drivers, etc.

There may be additional discs with apps and/or drivers.
:confused: For my newest laptop (from Toshiba), I had to make my own, using a utility that came preinstalled. This could have been (at least in part) because it was an ex-shop-display machine. 
Two of my other machines (another Toshiba laptop and an older Win98 machine) came with disks, and my Compaq machine came with a recovery partition.

---

### Post by doorknob60 on 2008-12-07
VB6 via Wine (looks like it works very well): [http://appdb.winehq.org/objectManager.php?sClass=version&iId=1325](http://appdb.winehq.org/objectManager.php?sClass=version&iId=1325)

Ulead Video Studio, not su much though: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=3348](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3348) BUT, you could probably use something like Kdenlive to edit videos, or you could use Virtualbox to virtualize a copy of Windows to use it.

Fruity Loops look like it could work pretty well, depending on the version though: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=178](http://appdb.winehq.org/objectManager.php?sClass=application&iId=178)

---

### Post by 5circles on 2008-12-07
> **eBoxNet said:**
> They don't give recovery cds anymore they are just create a recovery partition.

My new HP had one.

But they do give you the ability to create Recovery CDs/DVDs.  This is a good idea if you considering removing the Recovery Partition.  Sadly, my Recovery DVDs had problems, but I was able to get replacements from HP.

---

### Post by eBoxNet on 2008-12-07
i didn't get cds i just had the recovery partition on,my Toshiba laptop had cds and no recovery partition...i prefer to have both..anyways did you try to hit f10 on boot?

---

### Post by kewlpics on 2008-12-07
Try VirtualBox to install Windows on top of Ubuntu.

---

### Post by eBoxNet on 2008-12-07
its not so good idea i think to run video editing applications on a virtualbox.

---

### Post by russo.mic on 2008-12-08
Far better video editing available to you here than on windows.  

Check out OpenMovieEditor and mainly Kino.  Kino kicks the hell out of adobe premier.  

Russo

---

### Post by bluenova on 2008-12-08
> **russo.mic said:**
> Far better video editing available to you here than on windows.  

Check out OpenMovieEditor and mainly Kino.  Kino kicks the hell out of adobe premier.  

Russo

LOL, sorry as much as I love Ubuntu that is simply not true. There is nothing out there for any operating system that beats Adobe Premier, why do you think it has that price tag?

KDENLIVE currently offers the best Ubuntu solution for stability, features and ease of use since their 0.7 release, but you will need to compile it from source as there are currently no debs for it. This version is comparable to iMovie for the Mac.

---

### Post by eldragon on 2008-12-08
and instead of fruity loops, give hydrogen a go.

search for it with synaptics.

---

### Post by tvtech on 2008-12-08
> **Slim Odds said:**
> I keep seeing people say things like this, but it's just not true.

They give you something called a "recovery CD", which contains the operating system and some applications, drivers, etc.

There may be additional discs with apps and/or drivers.

IF you buy something other than an overpriced piece of junk.  say like you go buy an asus or a dell.  they give you A recovery image CD/DVD, they are legally obligated to because of their eula and windows new eula stating that each image is for a single PC.  They will argue but... they will eventually give in.  solution.  Buy an ASUS they give you the hdd auto image that vista creates and you can if you want to disable, and they also give you a reimage dvd with factory defaults at time of purchase.  So does dell.  

This is basically the same recovery image they put on your HDD.  Also you can call the company you purchased and with a little bit of irritation they can give you a recovery image CD/DVD.  This is an image and not a full OS install it will give you all the defaults that came when you purchased your computer. if your smart and back up to a recovery image with a product like norton ghost, there are many many others for commercial and non commercial use.  then you should have a recent update, supposedly vista now does this by default, so does OSX.  You should always keep your recovery image on a separate hdd from your primary install, because it is useless if you have a mechanical failure, every hdd is rated differently but expect a failure in about 4-5 years depending on usage.

---

### Post by tvtech on 2008-12-08
> **russo.mic said:**
> Far better video editing available to you here than on windows.  

Check out OpenMovieEditor and mainly Kino.  Kino kicks the hell out of adobe premier.  

Russo

clearly you need to take some classes on Adobe premier to learn how to use it.  KINO although being free is far inferior in many many aspects especially if you are trying to work in a professional environment.  MAC's final cut pro is the definitive video editing software.  Avid's software for windows is something of a spectacular piece but it's fallen out of favor due to the cost undercutting done by Apple. There are far more video editing systems that run on Windows than any other platform, since the single use silicon graphics machine main frame idea went out the window with the advent of low cost processing power.

---

### Post by russo.mic on 2008-12-23
> **bluenova said:**
> LOL, sorry as much as I love Ubuntu that is simply not true. There is nothing out there for any operating system that beats Adobe Premier, why do you think it has that price tag?

KDENLIVE currently offers the best Ubuntu solution for stability, features and ease of use since their 0.7 release, but you will need to compile it from source as there are currently no debs for it. This version is comparable to iMovie for the Mac.

I guess we just think differently.  I think premier is one of the worst editors in terms of interface and format compatiablity.  I run my video editing side of my business with almost exclusivly kino, going to final cut to sometimes render.

Still, adobe premier's price tag isn't the argument.  plenty of software that has quite a hefty price tag can be replaced with open source software and be beaten out,  Find a better argument.

Russo

---

