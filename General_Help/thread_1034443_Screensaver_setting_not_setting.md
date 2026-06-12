---
title: "Screensaver setting not setting"
date: 2009-01-08
forum: General Help
---

### Post by DougieFresh4U on 2009-01-08
I have set it so there is no screensaver and no power down (screen always on) Don't know what I did or removed but after 10 minutes screen goes black and I have not changed the settings. This started yesterday. What can I check to see what may be not working right?
Thanks

---

### Post by mwillams73 on 2009-01-09
Im sorta having the same problem, it seems to me that on mine ( intrepid) that its not recognizing the command but as of yet I havent been able to find a fix, I posted a thread for my problem as soon as someone gets back to me I'll try and give you hand with yours, until then keep us updated OK?

---

### Post by mwillams73 on 2009-01-09
Ok this comes from mssever, on one of my threads I asked for help with this and this is what I got,

from mssever,
I suspect that gnome-power-manager is the culprit. Try firing up gconf-editor and examining the keys under /apps/gnome-power-manager to see if things are as expected. g-p-m sometimes crashes on me, in which case odd power-related things happen (in some cases, my computer won't sleep when I expect it to.

It was simple for me I dont know about you , I dont know if this works or not as Ive just played around with it and set things the way id like them , in case you dont know how to get this running do this,

Type gconf-editor in your terminal, thats it. A new window should pop up then go where it says in the above paragraph and change a few of the settings, if and when I see that its worked for me I'll let you know exactly what I did but for now I wanna make sure i didnt screw up anywhere before i tell you what you should do. I really hope this helps you, and me.

---

### Post by mwillams73 on 2009-01-10
Ok so I set the gonf editor/actions all to nothing, that seemes to work for my pc shutting down by itself, but I was still having problems with display powering itself off. so I went gconf editor/timeout/sleep_computer_AC to 0, then timeout/sleep_display_AC to 0, hopefully this was the culprit, it was set to turn of the screen after 1200 seconds of inactivity. I hope this helps you!

---

