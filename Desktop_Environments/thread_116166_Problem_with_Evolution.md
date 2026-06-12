---
title: "Problem with Evolution"
date: 2006-01-12
forum: Desktop Environments
---

### Post by vificunero on 2006-01-12
Hi. I have this problem with evolution. I've just boot up my system but evolution doesn't work. Yesterday was fine. Here is what I have when I launch it:

> lorenzobo@vificulandia:~ $ evolution
adding hook target 'source'

(evolution:13276): Gdk-CRITICAL **: gdk_gc_set_foreground: assertion `GDK_IS_GC (gc)' failed


evolution 2.4.1-Oubuntu7 (breezy).

The programs loads but then it just stops. Any help? Thank's.

---

### Post by dcstar on 2006-01-12
[QUOTE=vificunero]Hi. I have this problem with evolution. I've just boot up my system but evolution doesn't work. Yesterday was fine. Here is what I have when I launch it:



evolution 2.4.1-Oubuntu7 (breezy).

The programs loads but then it just stops. Any help? Thank's.[/QUOTE]
Try renaming your .evolution directory, and start it up again.

If that works you had corrupted your profile (somehow), you will then have to move your old mail files from the renamed directory into the newly created .evolution directory.

---

### Post by vificunero on 2006-01-12
Hi, Thank's for your reply. I did as you suggested me but It didn't work out.
I've tried with another user and evolution works fine. So I guess there are other files I should look at in my home directory. I wonder which.:p

---

### Post by dcstar on 2006-01-12
[QUOTE=vificunero]Hi, Thank's for your reply. I did as you suggested me but It didn't work out.
I've tried with another user and evolution works fine. So I guess there are other files I should look at in my home directory. I wonder which.:p[/QUOTE]
Try renaming the various .gnome directories, if it fixes things then you may just have to re-tweak your desktop.

---

### Post by kaamos on 2006-01-12
You could try to rename this directory: ~/.gconf/apps/evolution/

---

### Post by vificunero on 2006-01-13
Thank's guys. I've just rebooted and everything is fine now. I don't know really why it didn't work.:???:

---

### Post by dcstar on 2006-01-13
[QUOTE=vificunero]Thank's guys. I've just rebooted and everything is fine now. I don't know really why it didn't work.:???:[/QUOTE]
There is an Evolution Server process that loads at startup, that may have had a problem (and your reboot fixed it).

---

