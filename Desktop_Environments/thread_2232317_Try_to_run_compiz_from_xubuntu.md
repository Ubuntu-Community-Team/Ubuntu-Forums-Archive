---
title: "Try to run compiz from xubuntu"
date: 2014-07-01
forum: Desktop Environments
---

### Post by mctiew on 2014-07-01
I believe I am running xfce with Ubuntu 14.04.

That is running fine.

But when I try to enable compiz by typing on the terminal window :-

compiz --replace ccp &

The xfwm4 got terminated ( replaced ? ) and I have left with opened windows without window frame/decoration. Looks like there is no window manager running. I checked fhat compiz is running.

What am I doing wrong ?

---

### Post by deadflowr on 2014-07-01
Most likely compiz is in fact running, however the window decorations plugin is most likely disabled.
If trying to run compiz, it's probably best to have it's tweak tool at the ready.
compizconfig-settings-manager

You can check to see what/which plugins are enabled and not enabled and resolve the differences from there.

---

### Post by mctiew on 2014-07-01
OK I got the window decoration by enabling window decoration plugin ***AND*** a few other WM functions. 

I tested the enhance desktop zoom, and it's OK. 

I configure 6 view port. But unable to switch view port even though I have enable the view port switcher and configure mouse button 4 and button 5 for switching viewport using mouse wheel scroll. 

Anyone ?

---

### Post by mctiew on 2014-07-01
I did additional configuration and also added other non-supported plugins, now the viewport switch using mouse wheel scroll is working.

And I configured multiple wallpapers and just to realize the desktop icons/launcher are all gone.

Seems from the internet posts need to do a source patch or something to get this working.

Anyone ?

---

### Post by mctiew on 2014-07-02
Found another problem when running compiz.

My VMWare workstation guest window is very small and not resizable to bigger.

After resizing the VMware window, the actual content of the guest drawable area remains small, even though the VMware window is bigger, ie the rest of the area becomes blank.

Switch back to xfwm4 removes the problem. 

Running using Virtualbox is OK with compiz however.

---

### Post by mctiew on 2014-07-02
I speak too soon. I found it VMware is taking the value of display setting in the ccsm. I delete the setting there and now the display is as good as when using xfwm4.

---

### Post by mctiew on 2014-07-02
How to make compiz autostart when system boots up ? 

Do I configure add a new autostart by using Setting Manager -> Session and Startup ?

---

### Post by xc3RnbFO8P on 2014-07-03
Yes, just add :
 
Name: Compiz
Command: compiz --replace

---

