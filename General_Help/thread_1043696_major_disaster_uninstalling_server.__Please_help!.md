---
title: "major disaster uninstalling server.  Please help!"
date: 2009-01-18
forum: General Help
---

### Post by quixote on 2009-01-18
A little knowledge is a dangerous thing.  I used sudo tasksel install lamp-server so I could test some web sites on my desktop before uploading.  However, php didn't work.  After searching, I found out I had missing packages, but when I tried to install them, I got messages about removing important stuff like mysql and apache2, which I didn't want to do!  So I thought I'd backtrack by using tasksel to remove.  ```
sudo tasksel remove lamp-server
```It started removing just about everything in my install!  Including gnome-desktop, nm-applet, audacity, brasero, and dozens of other things that have nothing to do with the lamp server!  And there was no way to stop it.  I couldn't open another terminal window to abort the process because that only gave me an error message.  After a few seconds of increasing panic, I just closed the terminal.  The connection between the desktop and the rest of the system is gone.  I still can't even open a terminal.

I've booted off a Hardy LiveCD (intrepid won't run on my hardware).  I know I could boot into rescue mode and issue commands that way, but I don't know which ones to give it!

Is there any way I can repair my system?  I hope so!

Thanks for any help you can give me!

---

### Post by aheckler on 2009-01-18
I would suggest rescuing whatever data you can, and then doing a fresh reinstall. It seems like it would take less time that way, but that's just my two cents.

---

### Post by DylanW on 2009-01-18
I accidentally did that once too, I think there's a log somewhere of what all's been uninstalled but i don't know the path and you'd spend a lot of time downloading and installing them all so just recover important stuff and reinstall

---

### Post by quixote on 2009-01-18
Reinstall, huh?  I was afraid that was going to be the answer.  At least I have /home on a separate partition.

Is that really, really my most efficient choice?  ??  :-(

Thanks for your answers, though!

---

### Post by aheckler on 2009-01-18
> **quixote said:**
> Is that really, really my most efficient choice?

I'm afraid so, but it won't take you too much time.

---

### Post by quixote on 2009-01-18
Okay.  Here goes.  Wish me luck ;-)

---

### Post by quixote on 2009-01-19
Just a sort-of progress report.  I had kde installed as well, and when I tried to reboot, that desktop came up by default instead.  Very intelligent of Ubuntu!  Unfortunately, all the programs I'd lost were still lost, and it didn't take long until I decided you were both right.  Reinstall.

Well, it's about a day later, and I have most of my system back.  I saved my xorg.conf file because I have weird graphics (ATI Mobility Radeon 7500).  But it turned out not to have the right settings in it!  :confused:

It took me *hours* to get my screen off that godawful 800x600 vesa fallback.  The secret is to use the "radeon" driver, and to make sure fglrx is purged from the system!

I'm still missing some stuff, but all in all it's been a real object lesson in what a good idea it is to have /home on a separate partition from / (ie root)!  I had to reinstall Thunderbird, Virtualbox, and Openoffice 3, but the settings were all as I'd customized them once the programs were up and running.  Nice. I wasn't looking forward to re-entering 10 persnickety settings for each of four mail accounts!  My virtual machines were right there too.  Reinstalling my old WinXP in vbox would have been awful!

So, I'm surviving.  Thanks for your suggestions. :D

---

