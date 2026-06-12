---
title: "How to remove the GUI?"
date: 2011-02-09
forum: Desktop Environments
---

### Post by latestbeats on 2011-02-09
Hi,
 
I'm a new user of linux and a few weeks ago i installed Ubuntu Server 10.10. And after a few day's i installed the GUI with: apt-get install ubuntu-desktop. But now, a few weeks later i want to remove the GUI again. How can i do this and is this possible?

---

### Post by vortmax on 2011-02-09
```

apt-get --purge remove ubuntu-desktop

```

---

### Post by latestbeats on 2011-02-09
Alright, I used the command in the terminal, but it seems not working... After rebooting my system i still having the GUI. :(
Whats the problem or i'm doing something wrong?

---

### Post by vortmax on 2011-02-09
what did it say when you ran the command ?

edit:

try:
```

sudo tasksel

```

uncheck "Ubuntu Desktop"
check   "basic ubuntu-server"

---

### Post by latestbeats on 2011-02-09
root@ubuntu:~# apt-get --purge remove ubuntu-desktop
Reading package lists... Done
Building dependency tree 
Reading state information... Done
The following packages will be REMOVED:
ubuntu-desktop*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 61.4kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 222615 files and directories currently installed.)
Removing ubuntu-desktop ...
[EMAIL="root@ubuntu"]root@ubuntu[/EMAIL]:~#
 
Edit:
 
I just tried tasksel, Ubuntu desktop was already unchecked and Basic Ubuntu-Server wasn't in the list.

---

### Post by mcduck on 2011-02-09
Yep, that's not gouin to remove anyhting else than the "ubuntu-desktop" metapackage itself.

Try running "*sudo apt-get autoremove*" to get rid of the packages installed as dependencies for "ubuntu-desktop. Meaning all the *actual* packages.

(you could also have ran "*sudo apt-get --purge autoremove ubuntu-desktop*" in the first place, but luckily autoremove should still do it's job just fine)

---

### Post by latestbeats on 2011-02-09
[EMAIL="root@ubuntu"]root@ubuntu[/EMAIL]:~# sudo apt-get --purge autoremove ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ubuntu-desktop*
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 61.4kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 222615 files and directories currently installed.)
Removing ubuntu-desktop ...
[EMAIL="root@ubuntu"]root@ubuntu[/EMAIL]:~#

After rebooting i still have the gui.
What's going wrong?:confused:

---

### Post by nothingspecial on 2011-02-09
Have a look at this page

Copy and paste the remove ubuntu bit, but make sure you delete the very end bit
```

&& sudo apt-get install kubuntu-desktop
```

or you will remove ubuntu but end up with kubuntu instead.

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)

---

### Post by latestbeats on 2011-02-09
Works great! I copied the code and pasted it in gedit, I deleted "&& sudo apt-get install kubuntu-desktop" and saved it as uninstal.sh. after that, i did "batch uninstal.sh" And it started to uninstall a lot of things. After rebooting i could login to the terminal. 
 
Thanks a lot for helping me!:D

---

