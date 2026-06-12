---
title: "New prob with package manager"
date: 2007-10-20
forum: Desktop Environments
---

### Post by sjoseph on 2007-10-20
I may have caused a problem but i was trying to get hplip to work, so i uninstalled it and when i tried to reinstall it, the package mgr wouldn't, said i needed hplip data and python 2.5.1, both of which are installed. i checked the pkg mgr and checked off all of the respositories. now when i try to open it i get:

E:Dynamic MMap ran out of room, E:Error occurred while processing python-dbg (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

any thoughts.

---

### Post by sjoseph on 2007-10-20
sjoseph@sjoseph-desktop:~$ sudo apt-get -f install
Password:
Reading package lists... Error!
E: Dynamic MMap ran out of room
E: Error occurred while processing python-dbg (NewVersion1)
E: Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages
E: The package lists or status file could not be parsed or opened.
sjoseph@sjoseph-desktop:~$ 

HELP PLEASE.......

---

### Post by jasbur on 2007-10-21
It sounds like a cache problem.

You could try issuing a
```
apt-get clean
```
in the terminal.

I also found this thread at linuxquestions.org on adjusting the cache size.
[http://www.linuxquestions.org/questions/debian-26/dynamic-mmap-ran-out-of-room-error-when-adding-new-apt-source-list-233417/](http://www.linuxquestions.org/questions/debian-26/dynamic-mmap-ran-out-of-room-error-when-adding-new-apt-source-list-233417/)

---

### Post by sjoseph on 2007-10-21
Thanks, tried that with no luck. Same message:
'E:Dynamic MMap ran out of room, E:Error occurred while processing python-dbg (NewVersion1), E:Problem with MergeList /var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_feisty_main_binary-i386_Packages, E:The package lists or status file could not be parsed or opened.'

oh boy, what have i done....

---

