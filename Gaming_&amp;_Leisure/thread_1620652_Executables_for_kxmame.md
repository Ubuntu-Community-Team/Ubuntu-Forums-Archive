---
title: "Executables for kxmame?"
date: 2010-11-13
forum: Gaming &amp; Leisure
---

### Post by lymphor on 2010-11-13
Hi everybody,
I'm using [COLOR=MediumTurquoise]**Ubuntu Studio 10.10**[/COLOR] and I'm having some problems with **kxmame**.
I previously used [COLOR=DarkOrange]**Ubuntu 10.04**[/COLOR] and had no problems with kxmame.
Before switching to U.Studio I backed up the home folder of Ubuntu 10.04.
Then, when in Studio, I installed kxmame and overwrote the .kxmame folder in home with the previously backed-up one.
The problem I have is _kxmame doesn't recognize as valid any of the executables I have_.
The message I get is:
```
no valid xmame/xmess executables found
```The directory of the executables is:
**usr/games **
 

And the files present in it are: 
 **gmameui **
 **xmame** <-- that is a link to **/etc/alternatives/xmame **
 **xmame.SDL** 
 **xmame.svgalib **
 **xmess**  <-- that is a link to **/etc/alternatives/xmess **
 **xmess.SDL **
 
None of these files is recognized by kxmame as valid (not even the 2 in /etc/alternatives/).

I thought maybe I'm missing some executable so I went to synaptic trying to install xmame-x (as you can see in the screenshot). Sadly once I try to apply this installation Synaptic tells me that it has to remove kxmame in order to install xmame-x.

Could you please help me?
Thank you in advance!:mrgreen:

---

### Post by Chema san on 2010-11-16
Hello,
I have had the same problem. I solved doing this:
1. Uninstall xmame-sdl
2.Enter to this page .Deb:
[http://ftp.debian.org/debian/pool/non-free/x/xmame/](http://ftp.debian.org/debian/pool/non-free/x/xmame/)
3.Install this archive:
xmame-sdl_0.106-2.1_i386.deb     21-Jun-2.008 21:02 9.4M

4. Update with the follwing:
xmame-sdl_0.106-3.2_i386.deb      06-Dec-2009 11:55 9.4M

Run kxmame. 
Go to settings/directories. 
In xmame/xmess executable add usr/games/xmame.SDL
I hope this work to you too.

---

### Post by disturbedite on 2010-11-16
you all can make your own choice, but it isn't advisable to use xmame. it is SUPER outdated. (at 0.106 when the latest version of mame is 0.140).

i recommend you use (sdl)mame and not xmame. it is up-to-date.

there are many frontends for it if you need a GUI. list of frontends: [http://rbelmont.mameworld.info/?page_id=163](http://rbelmont.mameworld.info/?page_id=163) (look for the section titled "Got any compatible front ends for Linux? OS X?").

i personally recommend QMC2 for a mame frontend.

---

### Post by lymphor on 2010-11-16
@[Chema san]("http://ubuntuforums.org/member.php?u=1188680"):
Man this just works!
Thank you SOOOOOOOOOOOOOOOOOOOO MUCH!
You're great, thanks! =D>

@[disturbedite]("http://ubuntuforums.org/member.php?u=228326"):
Thank you but some of those frontends are outdated, others have to be compiled and I don't know how to do it.
Untill there'll be a better solution for Kxmame or Gmameui (because I had the same problem with Gmameui) I'll use [Chema san]("http://ubuntuforums.org/member.php?u=1188680")'s solution. Thanks for your advice.

---

### Post by asun200 on 2010-11-18
Hello I tried chema san tip, but doesnt work, when i try to uninstall xmame.sdl, synaptic wanna uninstall kxmame as well  :((

---

### Post by asun200 on 2010-11-19
Well did it, yes uninstall kxmame and after install the 2 debs reinstall kxmame and is working, thank you, i didnt realize pass 6 months without mame lol  o/

---

