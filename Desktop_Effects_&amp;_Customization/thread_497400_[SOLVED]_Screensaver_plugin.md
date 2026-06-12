---
title: "[SOLVED] Screensaver plugin"
date: 2007-07-10
forum: Desktop Effects &amp; Customization
---

### Post by darek1176 on 2007-07-10
After the last update my screensaver plugin in compiz-fusion stopped working (it is enabled)? Anyone may know why? It used to work before the update. The rest works ok.

---

### Post by wconstantine on 2007-07-10
Same problem here. I'm sure they fix it with the next update. They come quite frequently.

---

### Post by darek1176 on 2007-07-10
Thanx, I will wait then. I hope it will be fixed. I tried to re-install compiz-fusion but it did not help

---

### Post by darek1176 on 2007-07-12
Yes, it is fixed with today's update...

---

### Post by Seine on 2007-07-14
Hmmm, I get updates daily on compiz fusion, but I haven't seen the screensaver plugin appear yet. And I still don't have the snow (snowflake?) plugin. What might be wrong?

---

### Post by wconstantine on 2007-07-14
> **Seine said:**
> Hmmm, I get updates daily on compiz fusion, but I haven't seen the screensaver plugin appear yet. And I still don't have the snow (snowflake?) plugin. What might be wrong?

You need the unsupported-plugins package. To get this fire up the terminal and write:

sudo apt-get install compiz-fusion-plugins-unsupported. Try with unofficial in the end if you wanna try out some more. Dunno what they do though. ;)

---

### Post by Seine on 2007-07-14
Ripper thanks! They're in the unofficial package.

---

### Post by fastpakr on 2007-07-31
This may be a separate issue - I'm not really sure.  With Fusion, if I enable the screensaver it doesn't seem to activate automatically based on the inactivity timer (set at 5 minutes, but I've tried 1 minute as well).  I can set a screen edge as a manual activation and that works fine.  It'll just never come on automatically.  Anybody have a suggestion on this?

---

### Post by madc on 2007-07-31
fastpakr...

read this:

[link]("http://ubuntuforums.org/showthread.php?t=195557&highlight=replace+gnome+screensaver")

and after that try this (helped me):

gconftool-2 --type boolean -s /apps/gnome_settings_daemon/screensaver/start_screensaver false

---

### Post by fastpakr on 2007-07-31
Thanks.  If I'm using the Compiz screensaver plugin, do I need to install xscreensaver from that thread, or stop at disabling the built in gnome screensaver?

---

### Post by madc on 2007-07-31
> **fastpakr said:**
> Thanks.  If I'm using the Compiz screensaver plugin, do I need to install xscreensaver from that thread, or stop at disabling the built in gnome screensaver?


no, you don'have to install xscreensaver, just stop the gnome screensaver...and compiz screensaver will automatically start!

---

### Post by deadlikeoscar on 2007-07-31
Worked for me as well. Thank you so much!

---

