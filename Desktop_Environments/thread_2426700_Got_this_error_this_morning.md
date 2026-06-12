---
title: "Got this error this morning"
date: 2019-09-12
forum: Desktop Environments
---

### Post by Autodave on 2019-09-12
Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic InRelease
Hit:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) bionic-security InRelease              
Hit:3 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-updates InRelease             
Hit:4 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) bionic-backports InRelease           
Hit:5 [http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu](http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu) bionic InRelease    
Get:7 [http://linux.teamviewer.com/deb](http://linux.teamviewer.com/deb) stable InRelease [9,388 B]               
Hit:8 [http://ppa.launchpad.net/openrct2/nightly/ubuntu](http://ppa.launchpad.net/openrct2/nightly/ubuntu) bionic InRelease        
Ign:6 [https://launchpad.net/graphics-drivers/ubuntu](https://launchpad.net/graphics-drivers/ubuntu) bionic InRelease           
Err:9 [https://launchpad.net/graphics-drivers/ubuntu](https://launchpad.net/graphics-drivers/ubuntu) bionic Release
  404  Not Found [IP: 2001:67c:1560:8003::8003 443]
Reading package lists... Done
E: The repository 'http://launchpad.net/graphics-drivers/ubuntu bionic Release' does not have a Release file.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.


Do I need to do anything about this?

---

### Post by CatKiller on 2019-09-12
Is this a machine that you've recently configured? The url you're using for the graphics drivers PPA is missing the ppa prefix: ```
deb http://ppa.launchpad.net/graphics-drivers/ppa/ubuntu bionic main
```

---

### Post by Autodave on 2019-09-12
No....this has been running 18.04 since it was released.  Is for the Nvidia graphics?  That was added about 2 months ago.

---

### Post by Autodave on 2019-09-12
I "unticked" that one.  The one that you posted as correct was already there.  I do not get the error now when doing the sudo apt-get update, but I still get the error message when booting up.

---

### Post by CatKiller on 2019-09-12
What's the error message when you boot?

The kernel module from the PPA isn't signed, so if you're using Secure Boot you'll get a warning message about that. You can either ignore that, turn off Secure Boot, or self-sign the module.

Unless the error message is something else, of course.

---

### Post by Autodave on 2019-09-12
It does not give me an error message: it just says that there is an error and gives me the option to report it or close the dialogue box.  I am not using secure boot.  How do I align the module?  (Never heard of that before.)

---

### Post by CatKiller on 2019-09-12
Those crash report messages could be about anything. And they're not always about a crash at the time you get the message. And if the bug report doesn't get acknowledged by some machine on the Internet somewhere it will keep nagging you about it forever. A recurrent message every time you log in could be about a single application crash weeks ago. /var/crash is where they get put, I think. 

Self-signing modules puts a Machine Owner Key in your UEFI certificate store. I did it once for the nvidia module and Virtualbox just to go through the process. It's a bit of a pain, but not too arduous.

---

