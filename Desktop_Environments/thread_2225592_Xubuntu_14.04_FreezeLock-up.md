---
title: "Xubuntu 14.04 Freeze/Lock-up"
date: 2014-05-22
forum: Desktop Environments
---

### Post by treeherder on 2014-05-22
Hello everyone,

I've been having trouble since installing Xubuntu 14.04 on release day on an old [Fujitsu Siemens Amilo Pi 2512]("http://www.notebookcheck.net/Fujitsu-Siemens-Amilo-Pi2512.9315.0.html") laptop.  It works perfectly for most of the time but then freezes and won't respond to keypresses (inc. CTRL+ALT+ESC or CTRL+ALT+F1).  The mouse cursor does move but at a greatly reduced rate and button presses seem to be ignored.  My only options seems to be a hard-reset or the SysRq "REISUB" sequence.
It seemed to happen when using Firefox on one of Google's sites (inc. YouTube but also just the web search), so I installed Chromium.  This hasn't resolved the issue, so maybe that was just a coincidence.  I suspected memory problems but Memtest reports no errors.

Thanks in advance...

---

### Post by mörgæs on 2014-05-22
What does **top** show when the computer almost-freezes?

---

### Post by treeherder on 2014-05-22
Thanks for the response. 
Nothing above 1.3% CPU. 
Just before lockup, kswapd0 appeared at the top of the list, and then dropbox. Third and fourth in the list is chromium-browser. 
Interestingly, top is still refreshing at full speed even though keyboard is dead and mouse is nearly.

---

### Post by Superkoop on 2014-06-06
Have you posted a bug yet? I have this same problem and it's really driving me nuts right now.
I will be using the computer as normal, then Xubuntu freezes. CPU is low, RAM is low. Mouse can move minimally however clicking does not work. I can't do an alt-ctrl-F2.

EDIT: Try changing your graphics driver. I was using the open source nouvou, now I'm using a proprietary option which seems to not freeze.

---

### Post by simonrodan on 2014-09-11
I've been experiencing the same issue. Once it locks up the keyboard is disbled; I have to ssh in from another machine and reboot.

---

