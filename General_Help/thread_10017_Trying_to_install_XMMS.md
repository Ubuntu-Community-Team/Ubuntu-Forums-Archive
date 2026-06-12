---
title: "Trying to install XMMS"
date: 2005-01-04
forum: General Help
---

### Post by pmshoop on 2005-01-04
Heya,

Fairly a newb to linux.  I've got ubuntu up and running smooth.  Even got Firefox and Thunderbird up and running as well as Real Player 10.  Just can't get XMMS to install right.  I downloaded it, and all the dependecies I could find.  I try to ./configure in a root terminal and I get the error 'no acceptable C compiler found in $PATH'  

Any input would be greatly appreciated.

Paul.

---

### Post by xkcdmagic8 on 2005-01-04
dude dude dude dude.............................................................................................!!!!
this is a debian system, you use APT-GET for synaptic heres the steps:

click computer->system confuguration->synaptic package manager

click tools->repositories and enable everything but the UNIVERSE ones (ask if u need help) (then click ok)

Hit the reload button and wait up for it.....

search for XMMS, click on the checkbox to install it (choose install)

click apply and there u go... does it for you !!

---

### Post by Adrenal on 2005-01-04
Yeh dude, simplify, debian is simple. Think of it as an intergrated download.com

---

### Post by LongTooth on 2005-01-04
pmshoop, you're going about this all wrong. First of all, Ubuntu is a Debian based distro. What does that mean? And how will that help? In a nutshell, apt-get or Synaptic. Ok, that still doesn't answer the question. These two programs will help you get just about all the programs you need with a simple CLI command of sudo apt-get install packagename. Or if you want to use a GUI, go to Computer> System Configuration> Synaptic Package Manager. Either will do the same thing. That is look for the package you want and install. Check out  [http://ubuntuforums.org/showthread.php?t=3713](http://ubuntuforums.org/showthread.php?t=3713) . In it you will add repositories (places to go to for packages/programs). Once that is done, you will be able to install by doing the simple CLI -command line interface - command of sudo apt-get install packagename. Or use the GUI -Graphical User Interface- Synaptic to do the same. 

To answer your question: To install Xmms do this. Open a terminal -Applications> System Tools> Terminal. Then key in 'sudo apt-get install xmms' without the quotes. Follow the instrutions. Simple. After that do a 'sudo apt-get install xmms-skins' for a choice of skins. To see if Xmms has been installed to to Applications> Multimedia. It should be there. If not, Alt+F2 will bring up a 'Run Application' window. Key in xmms. To really test it go to [http://www.kpft.org/](http://www.kpft.org/) . See 'Listen Here (for RealAudio) or Here (for mp3 Stream)'. Pick mp3. A box will ask you what to use. Pick 'Other'. Key in /usr/bin/xmms. If it works, the next time you do that check off the 'Do this every time' box. Xmms will then come on line everytime. Hope this helps.

P.S. Want some advice? If you are a newbie, say away from tarball for the time being. Wait until later to work with them. They still give me hell.

---

### Post by pmshoop on 2005-01-04
[QUOTE=LongTooth]pmshoop, you're going about this all wrong. First of all, Ubuntu i

P.S. Want some advice? If you are a newbie, say away from tarball for the time being. Wait until later to work with them. They still give me hell.[/QUOTE]


Hey thanks,

I am used to old school unix.  And yeah the tar balls....

Paul.

---

