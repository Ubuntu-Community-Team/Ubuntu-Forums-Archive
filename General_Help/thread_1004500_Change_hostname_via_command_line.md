---
title: "Change hostname via command line?"
date: 2008-12-07
forum: General Help
---

### Post by Repentless on 2008-12-07
Hey guys, when I set up my text based ubuntu system I used a hostname I didn't want. How do I change it via the command line? Thanks :)

---

### Post by Rocket2DMn on 2008-12-07
If you are looking to permanently change the hostname, edit the file /etc/hostname with your favorite command line text editor, using sudo/root privileges.  If you want a temporary adjustment, the "hostname" command can be used to set the host name until the next reboot.

---

### Post by iponeverything on 2008-12-07
edit:

```
sudo nano /etc/hostname

```
also:

```
sudo nano /etc/hosts

```

---

### Post by geirha on 2008-12-07
You should also change the corresponding entry in /etc/hosts
```
127.0.1.1    *hostname*
```

---

### Post by Rocket2DMn on 2008-12-07
+1 for /etc/hosts as well, though I believe this is subject to being overwritten by some of the system utilities.  You would need to edit the second line that looks like
```
127.0.1.1 *hostname*
```
otherwise, you may have problems when using sudo afterward (so maybe that file should be edited first).

---

### Post by CatKiller on 2008-12-07
It certainly used to be the case that if you changed the hostname in either one of the files but not the other, you then lost sudo powers to be able to open the other to change it. Which left you buggered. I don't know if this has been fixed.

Two possible solutions are to do it in a root session, either from the Recovery mode (single user) from GRUB or with ```
sudo -i
nano /etc/hostname
nano /etc/hosts
exit
``` or by logging in on two virtual consoles at the same time (Ctrl-Alt-F1 & Ctrl-Alt-F2) and opening one file in each before you save either of them.

---

### Post by panticz on 2010-03-10
sed -i 's|OLD_HOSTNAME|NEW_HOSTNAME|g' /etc/hostname
sed -i 's|OLD_HOSTNAME|NEW_HOSTNAME|g' /etc/hosts

---

