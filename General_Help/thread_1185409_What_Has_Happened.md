---
title: "What Has Happened ??"
date: 2009-06-12
forum: General Help
---

### Post by scythian on 2009-06-12
Hi,
 
I have installed Ubuntu v 8.04.2 (i386) Desktop edition on a PC with the following specs :-
 
3GHz Pentium 4 CPU
4GB RAM
ATI Radeon X1650 Pro AGP 8x 512MB graphics card
Intel D865GBF mobo
Hanns-G HX191D monitor native resolution 1280x1024
 
On first install all seems OK (though I avoid the ATI graphics driver as it caused problems before). But after I install all available updates via Update Manager and reboot, the screen resolution is stuck at 800x600, and it won't go any higher. Clicking 'Detect Monitor' does not have any effect.
 
I am puzzled - what is going on ?
 
:(

---

### Post by Legace on 2009-06-12
Post contents of **/etc/X11/xorg.conf** and also tell the optimum resolution and refresh rate of your monitor. If you don't know the optimum refresh rate, post the brand and model of your monitor.

---

### Post by scythian on 2009-06-12
Hi, thanks for reply. I have a Hanns-G HX191D monitor native resolution 1280x1024, with supported refresh rates 60-75Hz at that resolution - it displays clearest at 60Hz, so thats the refresh rate I always use.
 
To check if this is a reproducable problem I have re-installed Ubuntu completely. However now after updates + rebooting, the problem hasn't re-surfaced.
 
What I did get after a 2nd reboot was slightly elongated looking text display. So I switched from 60Hz to 75Hz, which corrected this, but now with a less clear looking display. Then I set it back to 60Hz and now it is fine, ie. not elongated, and crystal clear.
 
So this is fine for now as long as it stays that way, and I can try out this OS as I'm going along.
 
I assume there must be a few bugs with some graphics cards including the one I have (ATI Radeon X1650 Pro 512MB AGP).

---

### Post by H2SO_four on 2009-06-12
assumption correct, sadly.

---

### Post by kj6zd on 2009-06-12
Hi all,
yep I have been experiencing this for several years with different Distros, but never found anything that would make sense to me. 

:( I have to say that I am by no means a Linux expert!!

Recently, I can only tell that I had Ubuntu 8.10 release stuck in 640x480 and couldn't figure out how to get it to display in higher resolution, 
although the Boot screen would display in 1024x768 ??? 
Would be nice to know why this happens. 
With the latest release 9.04 everything went flawless on three different computer.
As said I have this observed on previous releases for several years with different Debian distros. 
In almost all cases a complete re-install fixed it, sometimes several re-installs. 
Have no clue why, although my best guess would be some configuration file is being used over again. 
Cheers,
Norbert:;)

---

