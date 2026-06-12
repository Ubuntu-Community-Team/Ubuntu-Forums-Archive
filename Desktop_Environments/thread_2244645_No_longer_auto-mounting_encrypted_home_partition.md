---
title: "No longer auto-mounting encrypted home partition"
date: 2014-09-17
forum: Desktop Environments
---

### Post by estex198 on 2014-09-17
**Edit: I forgot to mention I changed my password using passwd prior to rebooting and having problems. I was able to solve this problem by logging in under a terminal and entering 'ecryptfs-mount-private'. which prompted me for my old password, (not the ecryptfs passphrase as I had originally thought).

My encrypted volume (all data in my home folder) no longer mounts when I login. For instance, logging in through GDM gives me a black screen that idles for about a minute before loging me out and cycling back to the login screen. I'm pretty sure I made the mistake in some settings in a GUI app installed by default in UbuntuGnome. There was one setting in particular that had to do with automatically handling volumes, and I clicked it to indicate "Off". Now at bootup when Gnome starts loading, I get errors printed to the screen before the login screen appears, but the login screen appears so quickly I cant read these errors. I also noticed my /etc/fstab file was changed. I tried fiddling with the file but nothing helps. Logging in through a shell brings me to my home directory, but instead of my files I see two files:


Access-Your-Private-Data.Desktop
and...
READE.TXT


_Since I can't remember my passphrase, I'm not able to run ecryptfs-mount-private._


_What can I do to re-enable autohandling of my encrypted volumes when logging in through Gnome? I need to back up the data and then reset the passphrase._

---

