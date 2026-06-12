---
title: "Graphics Problem"
date: 2008-03-25
forum: Desktop Effects &amp; Customization
---

### Post by The New Guy on 2008-03-25
Well I have been running Ubuntu Gutsy with 3D effects for while now. I installed the restricted driver (which was my graphic card) after that I installed Xgl-Xserver and the resolution changed and it wouldn't not give the option to change it to the resolution that I desired, 1024 by 768, so I made a custom one. 

But now I decide to change it to plug and play after I did that I restart the computer when I the computer reboot  it get passed the splash screen but after that it just goes blank, well dark, and won't do anything after that.. I don&#8217;t know what I did, and I was wondering if anybody can help me to solve this? Please

[I][B]
[I]Notice: Plug and Play did not work once I installed Xgl-Xserver[/B]
[/I][/I]

---

### Post by phidia on 2008-03-25
For starters maybe post your /etc/X11/xorg.conf
If you saved your previous xorg.conf you could backup your current conf and revert to the older one-that might get you back to your desktop. Hope that helps.

---

### Post by The New Guy on 2008-03-25
Thanks for the reply but I did not make the back up for it because I don't know how to do it. I also forgot to mention that uninstall xgl-xserver.

---

### Post by phidia on 2008-03-25
You can create a new xorg.conf by opening a shell and typing "sudo dpkg-reconfigure xserver-xorg"
To open a shell press Alt+Ctrl+F1 together. Have your video card and monitor specs at hand.

---

### Post by The New Guy on 2008-03-25
Do you want me to install Xgl-Xserver again and try to do "sudo dpkg-reconfigure xserver-xgl," because like I said I don't  have xgl-xserver installed?

---

### Post by The New Guy on 2008-03-26
**Great News I soleved the Problem and now I login like nothing happend. Thanks for everything Phidia I really appreciat it.:guitar:**

---

### Post by sandeeps2 on 2008-03-27
hey new guy how did you solve the problem,. i have the same problem , i am not able to set it to the desired resolution and if i do set it to 1280* 1024 the screen starts to flicker in between a lot,

---

