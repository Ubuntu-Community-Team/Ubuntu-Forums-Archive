---
title: "Uninstallation error"
date: 2009-06-22
forum: General Help
---

### Post by Seeking Nothing on 2009-06-22
I've got an error when I try to uninstall things that reads "E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report." when I enter that into the terminal I get the following error, "dpkg: parse error, in file '/var/lib/dpkg/updates/0004' near line 14 package 'labyrinth': EOF during value field 'Description' (missing final newline)".

I'm running Ubuntu 9.04 as a second OS (with Vista being the main one).

 What do I do?

Let me know if I'm not giving enough technical detail.

---

### Post by Therion on 2009-06-22
Open a Terminal (Applications/Accessories).

Paste in:```
sudo dpkg --configure -a
```

---

### Post by Seeking Nothing on 2009-06-22
When I do that I get the following:

"seekingnothing@ubuntu:~$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0004' near line 14 package `labyrinth':
 EOF during value of field `Description' (missing final newline)"

---

### Post by michy99 on 2009-06-22
What is the output of these two commands?```
ls -l /var/lib/dpkg/updates/
cat /var/lib/dpkg/updates/0004
```

---

### Post by Seeking Nothing on 2009-06-22
```
ls -l /var/lib/dpkg/updates/ 
```

total 24
-rw-r--r-- 1 root root 108 2009-06-22 16:19 0000
-rw-r--r-- 1 root root 824 2009-06-22 16:19 0001
-rw-r--r-- 1 root root 817 2009-06-22 16:19 0002
-rw-r--r-- 1 root root 121 2009-06-22 16:19 0003
-rw-r--r-- 1 root root 641 2009-06-22 16:19 0004
-rw-r--r-- 1 root root 634 2009-06-22 16:19 tmp.i



```
cat /var/lib/dpkg/updates/0004
```

Package: labyrinth
Status: purge ok config-files
Priority: optional
Section: gnome
Installed-Size: 588
Maintainer: Daniel Holbach <daniel.holbach@ubuntu.com>
Architecture: all
Version: 0.4.0-0ubuntu1
Config-Version: 0.4.0-0ubuntu1
Depends: python, python-cairo (>= 1.0), python-central (>= 0.6.1), python-glade2, python-gnome2 (>= 2.12), python-gnome2-desktop (>= 2.14), python-gobject (>= 2.10), python-gtk2 (>= 2.8)
Description: lightweight mind-mapping tool
 Labyrinth is a lightweight mind-mapping tool, written in Python using Gtk
 and Cairo to do the drawing. It is intended to be as light and intuitive as
 possible, but still provides

---

### Post by michy99 on 2009-06-22
Try running these commands:```
sudo rm /var/lib/dpkg/updates/0004
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by Seeking Nothing on 2009-06-22
Thanks, that seemed to work.

Do you have any suggestions as to where I could go to better understand what you had me type in/why you told me to type in those specific commands?

Sorry for being a bit of a newb, but hey. We all start out new sometime.

---

### Post by michy99 on 2009-06-22
The first two commands were mainly because I was curious as to what was in that file and that directory, because that directory is empty on my system. Apparently they are temporary files created during installation/uninstallation. The 0004 file got corrupted somehow, so we just deleted it and tried again.

Most of what I learned I got right here reading these forums. When I see something I've seen before, I try to help out if I can.

---

