---
title: "Wine programs menu missing"
date: 2010-10-15
forum: Desktop Environments
---

### Post by ouff on 2010-10-15
I'm currently using Ubuntu 10.10 and the version of Wine in the standard repository.  In the past, when I've installed wine, it automatically gave me a Programs menu from which I could launch all the Windows programs I installed.  That menu is now missing.  I tried uninstalling Wine, removing the ~/.wine folder, and removing all references to wine and wine programs in ~/.local/share... with no effect.  I can't get the Programs menu to come back.  Any suggestions?

---

### Post by DavMag on 2010-10-16
What version of wine are you using, I'm currently using 1.3 and the programs I've loaded under wine show up in the menu. I am however trying to figure out how to get wine to read the cd rom while I'm running the program, so it can verify the cd. I have an Everex gbook that is running on a VIA 1.7 CPU with 2 gig of ram. Ubuntu10.10, trying run Warcaft2 it. At the time I'm writing this I'm currently downloading StarCraft from battlenets website. Trying to also run it under wine, I was able to get Diablo2 to download and install on a linux box but the machine was to old for it to be playable. If anyone can tell me how to solve my cd mount problem under wine would appericate.

---

### Post by claracc on 2010-10-17
I have wine 1.2 in lucid lynx upgraded from karmic koala.

I think i have the same problem with wine.

Under programs there is only notepad and I cannot put there the other .exe I have.

I have to go under exploring C:\ --> program files --> folder where is the program --> click on .exe.

I don't know how to put the .exe under wine --> programs. 

Perhaps it is not possible with this wine version?

---

### Post by sendblink23 on 2010-10-17
> **claracc said:**
> I have wine 1.2 in lucid lynx upgraded from karmic koala.

I think i have the same problem with wine.

Under programs there is only notepad and I cannot put there the other .exe I have.

I have to go under exploring C:\ --> program files --> folder where is the program --> click on .exe.

I don't know how to put the .exe under wine --> programs. 

Perhaps it is not possible with this wine version?

I would honestly give up that really  old wine, and get the latest one... from their repo:

> Alternative Command Line Instructions for Installing Wine:

It is also possible to add the Wine PPA and install via the terminal. This may be useful on Kubuntu, Xubuntu, and other Ubuntu derivatives.

sudo add-apt-repository ppa:ubuntu-wine/ppa

Then update APT's package information by running 'sudo apt-get update'. You can now install Wine by typing 'sudo apt-get install wine1.3'.

---

### Post by ouff on 2010-10-19
I found a solution that worked for me in this thread: [http://ubuntuforums.org/showthread.php?t=811623](http://ubuntuforums.org/showthread.php?t=811623)

I now have my programs menu back and all menu items are there.

---

