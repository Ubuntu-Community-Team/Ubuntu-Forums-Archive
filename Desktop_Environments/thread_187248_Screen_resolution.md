---
title: "Screen resolution"
date: 2006-06-02
forum: Desktop Environments
---

### Post by vidak on 2006-06-02
Do you know how screen resolution can be changed in KDE?
I've modified the xorg.conf file using configure-debian to have more resolutions, but that still didn't help. After pressing Ctrl Alt +/- nothing happens... 
any ideas?

---

### Post by Jucato on 2006-06-02
configure-debian?don't you mean
```
sudo dpkg-reconfigure xserver-xorg
```
Try using that, then restart your X server by pressing ctrl+alt+backspace.

---

### Post by vidak on 2006-06-02
well, it does practically the same. configure-debian gives a menu-based method to configure different packages, including xserver-xorg. So using configure-debiad does exactly the same thing as dpkg-refconfigure.

---

### Post by vidak on 2006-06-02
The problem has been solved meantime - I ran the config again, and restarted X one more time: and there are three resolution modes... I would like to know just why didn't work this all the time until now...

---

### Post by Christopher on 2006-06-03
I ran  sudo dpkg-reconfigure xserver-xorg in console to fix my screen resolution and i get this "sudo: timestamp too far in the future: Jun  3 02:57:17 2006"

Any ideas? Thank you in advance.

---

### Post by vidak on 2006-06-05
It seems a sudo-problem, not a dpkg-reconfigure - problem...
Maybe you could check the date of the sudo timestamp, located in /var/run/sudo (you need superuser privileges to look in this directory)...

Does this help?

---

### Post by Christopher on 2006-06-05
[QUOTE=vidak]It seems a sudo-problem, not a dpkg-reconfigure - problem...
Maybe you could check the date of the sudo timestamp, located in /var/run/sudo (you need superuser privileges to look in this directory)...

Does this help?[/QUOTE]

I fixed my date & time again and its working now, so im not sure what the issue was.

---

