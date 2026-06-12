---
title: "Beryl and Totem"
date: 2007-02-23
forum: Desktop Environments
---

### Post by juantovarm on 2007-02-23
I have been trying so watch some videos on totem while running beryl desktop, i had terrible results, the video screen would just go black, i had to go full screen, and back to normal screen and back to full screen to see something of the video. I went back to my normal 2d desktop, tried totem out, and voilá, everything works perfectly. Has anyone had similar problems? Any ideas?:confused: 

system conf: 
Intel D865Gsa MB
pentium 4 2.66
1.5 giga ram


Thanks

---

### Post by yemu on 2007-02-27
i have similar problems but i have no idea how to fix it

---

### Post by pins2u on 2007-03-15
In terminal, enter following code.

gstreamer-properties

It will open up the multimedia system window.

Click video tab, then choose X Window System (No Xv) for the Default Video Plugin.
Click Test button and make sure you see the player shows the picture. Then Close.

That's it, Enjoy your Totem again. :)

---

### Post by alexef on 2007-03-25
Thanks pin2u!
Same problem for me, solution worked smooth!

---

