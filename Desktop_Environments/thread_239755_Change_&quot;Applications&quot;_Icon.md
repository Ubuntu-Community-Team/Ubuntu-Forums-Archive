---
title: "Change &quot;Applications&quot; Icon?"
date: 2006-08-19
forum: Desktop Environments
---

### Post by PathSpace on 2006-08-19
I am not particularly crazy about the Ubuntu icon by "Applications" in my main GNOME menubar.  Is there any way to change it?

---

### Post by meng on 2006-08-19
[http://ubuntuforums.org/showthread.php?t=208457](http://ubuntuforums.org/showthread.php?t=208457)

---

### Post by PathSpace on 2006-08-19
Oh, wow, thanks.  :D

---

### Post by meng on 2006-08-19
Good luck with it. Feel free to complain if it doesn't work.

---

### Post by PathSpace on 2006-08-19
> **meng said:**
> Good luck with it. Feel free to complain if it doesn't work.

Hmmm...I might take you up on that offer, because it didn't work.  :p  Lol.  

I followed the directions, but still no GNOME foot.  :mad:

---

### Post by meng on 2006-08-19
Okay, well I am going to try the following (for fun). It is based on the directions here, but is a little more straightforward/foolhardy:
[http://doc.gwos.org/index.php/Gnome_Icon_Dapper](http://doc.gwos.org/index.php/Gnome_Icon_Dapper)

cd /usr/share/icons/hicolor/48x48/apps/

sudo mv distributor-logo.png distributor-logo.backup.png
sudo cp gnome-main-menu.png distributor-logo.png

and either
killall gnome-panel
(or else a relogin)

I can tell you if it works or no.

EDIT: And the answer is an emphatic NO! I must be messing around with the wrong icons ...

---

