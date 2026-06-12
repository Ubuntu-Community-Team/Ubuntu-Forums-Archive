---
title: "After most recent updates, another desktop broken"
date: 2015-10-31
forum: Desktop Environments
---

### Post by stevecro2 on 2015-10-31
Once upon a time, I started having trouble getting Compiz desktop to load up, with distorted video, etc., as I can remember. After posting some info here, was advised that for the amount of memory that I had at the time, I didn't have enough memory to run Compiz anyway (only had 1G back then). Switched to running Metacity and started to like it. Also, since then, have increased memory to 4G. 

Now after latest set of updates,  even with the more memory, can't get Compiz or Metacity to work. After putting in password, just get color background that was surrounding the login box. No wallpaper, no icons, nothing. Tried starting up with next oldest kernel from GRUB menu and that doesn't help. If I log into a text console, I can see that all my files (documents, etc.) are still there. The only thing that works for Gnome is the basic Gnome option, and that's what I'm running Chrome from right now to get to this forum. Would like to get Metacity back. Any ideas are appreciated!

---

### Post by Bucky Ball on 2015-10-31
In the CLI (text screen) run a full update and upgrade and see if that helps or posts any errors.

```

sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

This will NOT upgrade your current release to a newer one. Post any anomalies (between code tags, see last link in my signature). How much memory do you now have and which release of Ubuntu are you using?

---

### Post by stevecro2 on 2015-11-01
Sorry, should have mentioned running 14.04 LTS; memory got upgraded to 4G a few months ago.

First ran just today's batch of updates that popped up in what I still could run (basic Gnome). After this, MetaCity came up OK one time. Not being able to "leave well enough alone" ;), I tried running Compiz and ability to log into desktop (Compiz or MetaCity) went away again.

Next ran the 4 recommended steps (last one actually said that there was nothing to do, but first three steps worked on some packages), rebooted, and now MetaCity is back. If it stays, I'm happy. I will keep an eye on things for a day or two and post if a problem, thanks again!

---

### Post by Bucky Ball on 2015-11-01
Great news. If things are good after twelve hours or so, please mark as solved to help others (see first link in my signature). Good luck. :)

---

