---
title: "GNOME Panels Deleted"
date: 2011-11-05
forum: Desktop Environments
---

### Post by Seth Meyers on 2011-11-05
Hi, this is my first post, so let me know if I'm doing anything wrong.

I'm an advanced computer user but I'm somewhat unfamiliar with Linux. My problem: I deleted my GNOME panels to switch to a more eye candy CairoDock. Now I'm longing for the days of a fresh install environment. I haven't been able to do ANYTHING to restore them. I tried to get a freeware called Panel Restore, but this is no longer available anyplace I can find. I've googled and regoogled, and tried endless terminal commands but to no avail. Is there any master reset that takes everything back to a fresh install? I don't care if I lose files, I don't really have any on this computer.

Here are my system details if that helps:

I'm running Ubuntu 10.10 on a Lenovo T20. I've got a 20GB hard drive and 256 MB of RAM. Yep, it's ancient, but it's all I've got.

Please help me, I'll be forever in your debt lol. :)
Thank You!

---

### Post by werewolves on 2011-11-05
Maybe:
[http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/](http://linuxfud.wordpress.com/2007/02/14/how-to-reset-ubuntugnome-settings-to-defaults-without-re-installing/)

---

### Post by AlexDudko on 2011-11-05
Remove your gnome config. folder (in gnome 2 it's usually **.gconf**) and relogin.

---

### Post by Seth Meyers on 2011-11-05
> **AlexDudko said:**
> Remove your gnome config. folder (in gnome 2 it's usually **.gconf**) and relogin.
How exactly do I get to this file?

---

### Post by AlexDudko on 2011-11-05
It's a folder, not a file. Open terminal, and being in your home directory run
> rm -R .gconf

---

### Post by Seth Meyers on 2011-11-05
> **AlexDudko said:**
> It's a folder, not a file. Open terminal, and being in your home directory run
Thanks for taking the time to help me. But I just got this message when I ran it in Terminal: 

*rm: cannot remove `.gconf': No such file or directory*

Any ideas? I'm stumped. :)

---

### Post by Seth Meyers on 2011-11-05
OK, it's fixed now since I relogged in! Thank you guys so much. This is another example of the superiority of a community based OS over a giant corporately owned OS. I see how helpful you guys are!

Thank you!

---

