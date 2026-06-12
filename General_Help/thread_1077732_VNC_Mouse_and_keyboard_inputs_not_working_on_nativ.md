---
title: "VNC: Mouse and keyboard inputs not working on native X server"
date: 2009-02-22
forum: General Help
---

### Post by composites on 2009-02-22
I'm trying to set up a headless pc/file server and have been using vnc to control it. If I use vnc to start a new X server :1, then everything works fine, but I can't see/change any current processes. 

When I use vnc to view the native X server :0, it acts almost like a view-only mode where I can move the mouse, but not click on anything or input anything using the keyboard. Any ideas what is causing this?

---

### Post by composites on 2009-02-23
bump..

---

### Post by DaveWalz on 2009-09-05
You may have figured this out already, but just in case someone was searching this thread this answer may help.

First, let's assume you have an Nvidia Card, and have installed the drivers for said card.  Then let's assume you jacked up the 'appearance' to either 'normal' or 'maximum'.  You have?  Then here is the answer: Switch all special appearance to off ( the first choice).  Now try VNC remotely.  It works!  Seems to be an issue with the Nvidia driver and VNC. I am no expert, but hopefully that helped someone else who stumbled upon this thread as I did before I figured this out for myself.

---

### Post by lzebra on 2010-09-17
Thank you Dave Walz. I had the same problem today and your solution fixed it. SWEEET!):P

---

