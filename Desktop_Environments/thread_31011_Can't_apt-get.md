---
title: "Can't apt-get"
date: 2005-05-01
forum: Desktop Environments
---

### Post by pterandon on 2005-05-01
```
root@ubuntu:/home/greg # sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kubuntu-desktop
root@ubuntu:/home/greg # sudo
usage: sudo -K | -L | -V | -h | -k | -l | -v
usage: sudo [-HPSb] [-p prompt] [-u username|#uid]
           { -e file [...] | -i | -s | <command> }
root@ubuntu:/home/greg # sudo apt-get install kubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package kubuntu-desktop
root@ubuntu:/home/greg #
```

This is a failed attempt to follow the advice at:
[https://www.ubuntulinux.org/wiki/InstallingKDE](https://www.ubuntulinux.org/wiki/InstallingKDE)

which says to do what I tried.

---

### Post by az on 2005-05-01
Is the universe repo available?  (uncomment it in your sources.list)

sudo apt-get update
sudo apt-get install kubuntu-desktop

---

### Post by pterandon on 2005-05-01
What's a sources.list

Where's something that lets me search the computer for a given filename?

The second command doesn't work, perhaps because I haven't done your sources.list suggestion yet.

---

### Post by duff on 2005-05-01
[QUOTE=pterandon]What's a sources.list[/QUOTE]
# cat /etc/apt/sources.list

[QUOTE=pterandon]Where's something that lets me search the computer for a given filename?[/QUOTE]
# find <starting directory> -name '<filename>'

---

### Post by abhaysahai on 2005-05-06
You may even open synaptic and enable the repositories.

"sudo gedit /etc/apt/sources.list "

is byfar the easiest method.

Regards,
Abhay

---

