---
title: "Which version of KDM is in the Lucid repo?"
date: 2011-02-26
forum: Desktop Environments
---

### Post by x1a4 on 2011-02-26
Hi,

Which version of KDM is in the Lucid repository?  Also, if using KDM in Lucid, is the following configuration of VTs possible?  

VT 1-4 getty
VT 5-7 KDM
VT 8-9 free
VT 10-12 logs

Thank you.

---

### Post by Krytarik on 2011-02-26
[http://packages.ubuntu.com/lucid-updates/kdm](http://packages.ubuntu.com/lucid-updates/kdm) turns out "4.4.5".

Sorry, I don't know exactly what you are meaning by the other one.

---

### Post by x1a4 on 2011-02-26
> **Krytarik said:**
> [http://packages.ubuntu.com/lucid-updates/kdm](http://packages.ubuntu.com/lucid-updates/kdm) turns out "4.4.5".
Thank you.

> Sorry, I don't know exactly what you are meaning by the other one.

A Virtual Terminal (VT) also called a [Virtual Console (VC)]("http://en.wikipedia.org/wiki/Virtual_console"), is a means for an operating system to display interfaces--text or graphic.  At present (on Hardy) I have my VTs configured to run agetty (alternative getty) on VTs 1 through 4,  GDM on VTs 5 through 7, with 8 and 9 empty and some logs on VTs 10 through 12.  What this means is that when I press Ctrl+Alt+F1-F4 I will see a text log-in screen (shown by agetty) which will allow me to log-in to a command shell: tcsh in my case.  If I press Ctrl+Alt+F5-F7 I will see a graphical log-in screen allowing me to log-in to a graphical shell: In my case that's Xfce, although I sometimes use other GUIs also.  If I press Ctrl+Alt+F10 I will see User logs, Ctrl+Alt+F11: Daemon logs, Ctrl+Alt+F12: Kernel logs. 

I want to upgrade Hardy to Lucid but changes made to GDM will make this setup impossible.  I am wondering if it's possible to do this with KDM.  If so, I can upgrade to Lucid and replace GDM with KDM.

---

### Post by Krytarik on 2011-02-26
Thanks for clearing up. Though I do know the term VT, I've never seen such an complex usage, sounds useful/productive. ;-)

As you might guess, I have no idea if KDM is capable of doing that. I only use GDM, in a basic, untweaked way.

---

