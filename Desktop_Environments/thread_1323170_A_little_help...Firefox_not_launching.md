---
title: "A little help...Firefox not launching"
date: 2009-11-11
forum: Desktop Environments
---

### Post by acrimonious on 2009-11-11
I'm on Ubuntu (Hardy Heron) 64-bit and for some reason I can't get my Firefox to launch. My Firefox 32 (that I'd installed a while ago to get Flash to work) is working fine. I think there's something wrong with the Launcher or symlink but I'm not sure. Here's what I get from the terminal:

rick@Desktop:~$ firefox
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0
bash: firefox: command not found
rick@Desktop:~$ sudo apt-get install firefox-3.0
[sudo] password for rick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
firefox-3.0 is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-2.6.24-21 linux-headers-2.6.24-21-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rick@Desktop:~$ firefox
The program 'firefox' is currently not installed.  You can install it by typing:
sudo apt-get install firefox-3.0
bash: firefox: command not found

Any help is appreciated.

---

### Post by klemes on 2009-11-11
Try giving firefox3 or firefox-3.5 in the console.

---

### Post by acrimonious on 2009-11-11
No luck. 

rick@Desktop:~$ firefox3
bash: firefox3: command not found
rick@Desktop:~$ firefox-3.5
bash: firefox-3.5: command not found

Here's what I get if I try to launch it from the desktop:

There was an error launching the application.

Details: Failed to execute child process "firefox" (No such file or directory)

---

### Post by klemes on 2009-11-11
Maybe then it is best to remove firefox and then reinstall it from the start.

---

