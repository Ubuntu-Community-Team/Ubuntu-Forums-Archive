---
title: "Ring switcher/Compiz settings help"
date: 2007-08-24
forum: Desktop Effects &amp; Customization
---

### Post by detroit/zero on 2007-08-24
There were some update to compiz withing the last day or two. I just rebooted my laptop and noticed that some of the compiz settings windows have changed, and a number of my keybindings have been reset.  (I do have trevinos repo enabled, btw..)

Specifically, withing the ring-switcher preferences window, there is a new keystroke-entry process. The defaults that appear there don't work at all, and when trying to select a new key combination, the "select keys"  notification never goes down, and no matter what i press, it becomes my new "next window" key and sends the ring switcher into action.

Has anybody else had this happen since the last update? Is there an easy fix, or is it something that will have to wait until a bug-fix comes out?

---

### Post by zero244 on 2007-08-24
I didn't know Compiz did the Ring Switcher. To answer your question I haven't had Compiz reset like your describing.
I really haven't used compiz that much......>I prefer Beryl.

---

### Post by filologen on 2007-08-25
I have similar problems (also before todays or yesterdays update). My solution has simply been to edit the defaults in the configuration file for ring switcher by doing "sudo emacs '/usr/share/compiz/ring.xml'"

---

### Post by detroit/zero on 2007-08-25
I tried editing the config file, but it doesn't seem to have worked for some reason.

Luckily, as I reboot my system, there appears to be some updates to compiz waiting to be downloaded, so I'm hoping this'll take care of it.

---

### Post by detroit/zero on 2007-08-25
Yes, yes.. the update was the cure.

Problem solved.

---

