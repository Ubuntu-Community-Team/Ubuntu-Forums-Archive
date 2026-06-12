---
title: "I can't login after re-installing nautilus"
date: 2010-04-13
forum: Desktop Environments
---

### Post by JJ_save on 2010-04-13
Hi, this is my first post. I wasn't sure where to put this question, but since it involves Nautilus, I'll post it here.

After installing [Nautilus-Elementary]("http://www.webupd8.org/2010/01/nautilus-elementary-simplified-nautilus.html"), and deciding i didn't like it too much, I decided to go back to original Nautilus. So I uninstalled Nautilus through the package manager and then re-installed it.

I rebooted my computer, and now I can't seem to get past the login stage. I get asked for a user-name and password (which i was never prompted to do before), and when i enter it, nothing. The Ubuntu loading page will appear like it's loading, but i just end up back at the login box. 

I'm kinda at my wits-end here and I don't what to do. Right now I'm using a Linux Mint LiveCD to get around this.

My computer runs Ubuntu 9.10. I really hope there is a way to fix this problem without having to format my computer.

Thanks in advance.

---

### Post by MooPi on 2010-04-13
Nautilus carries large gnome dependencies and uninstalling and reinstalling may have borked the whole mess. You'll need to boot to recovery mode to correct.
At boot prompt hit the shift key to enter grub. While in recovery drop down to > dpkg repair broken packages Then try a reboot and see if this corrects the problem. If not boot back to recovery mode and drop down to root shell. ```
apt-get autoremove
``````
apt-get clean
``````
apt-get remove ubuntu-desktop
``````
apt-get update
``````
apt-get install ubuntu-desktop
```Hopefully this will install the desktop again and clean up hanging programs.

---

### Post by JJ_save on 2010-04-13
I tried doing what you said, Moopi, but i fail to update since my wireless internet connection is not found. Is there anyway I can setup a wireless internet connection through the terminal?

---

### Post by MooPi on 2010-04-13
Your going to need your install CD.
Boot to recovery mode and drop to root shell.
```
apt-cdrom add
```This should add your CD to the source list so you can make the changes.

---

