---
title: "How to undo 'Desktop Effects&quot;?"
date: 2007-06-24
forum: Desktop Effects &amp; Customization
---

### Post by Cushie on 2007-06-24
I tried to add Desktop Effects starting with Wobbly windows and Ubuntu 7.04 feisty.  I was given 30 seconds to make my mind up so I answered OK as I saw nothing disastrous.  However I can't get proper responses from my mouse and so cannot access the menus and preferences to undo these effects.  Help would be appreciated to get back original desktop.

Am I over optimistic in expecting these effects with Nvidia GeForce4 Mx4000 AGPx8 video card or is my set up in error?  I have just recently managed to get the resolution set correctly and the driver looks OK.  Are there any temporary tests I can try?

---

### Post by jhaubrich on 2007-06-24
there is no reason you video card should  have trouble.  It doesn't take allot to run desktop effects.

 alt-F2 will bring up a prompt. type: gnome-terminal. once you have a terminal window type: ```
killall compiz
```
I think that is the right process.  I dont have desktop-effects installed anymore so I cannot  check. ```
ps -lA 
```will give you a list of processes.

hope that helps.


helpful tip:
ctl-altF(1-6) will drop you into one of six virtual terminals. ctl-alt-F7 will get you back.

---

### Post by Cushie on 2007-06-26
Thanks jhaubrich, killall did the trick.
Cntl +Alt + F works fine, will try F7 next time
You believe my card can execute the desktop effects so I will do some further investigating into 'compiz' and try and keep out of trouble!

---

