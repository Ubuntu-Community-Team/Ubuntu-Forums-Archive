---
title: "I've finally broken something.... please help!"
date: 2007-12-26
forum: Desktop Environments
---

### Post by fizikz on 2007-12-26
I think the main problem right now is with dkms. I tried installing the .deb from here: [HTML]http://linux.dell.com/dkms/[/HTML] however, when I was originally installing it, I had the option to keep a certain file (I don't remember the filename) or replace it with the one from the .deb. I chose to keep the one already installed, and subsequently the installation failed. If I run the deb again, it doesn't ask me that question anymore, and just fails. Now when I try to install some things from Synaptic package manager, it fails because of a problem with dkms. 

Here is the error I get when trying to install the dkms .deb file:

```
#  dpkg -i dkms_2.0.17.5-0ubuntu1_all.deb
Selecting previously deselected package dkms.
(Reading database ... 156996 files and directories currently installed.)
Unpacking dkms (from dkms_2.0.17.5-0ubuntu1_all.deb) ...
Setting up dkms (2.0.17.5-0ubuntu1) ...
invoke-rc.d: initscript dkms_autoinstaller, action "start" failed.
dpkg: error processing dkms (--install):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dkms

```

Help would be greatly appreciated!

---

### Post by taurus on 2007-12-26
Try something like

```
sudo dpkg -r dkms_2.0.17.5-0ubuntu1_all
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by fizikz on 2007-12-26
Here is the output of the first two commands:

```
stephen@SSG1:~$ sudo dpkg -r dkms_2.0.17.5-0ubuntu1_all
Password:
dpkg - warning: ignoring request to remove dkms_2.0.17.5-0ubuntu1_all which isn't installed.
stephen@SSG1:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking, 0B of additional disk space will be used.
Setting up dkms (2.0.17.5-0ubuntu1) ...
invoke-rc.d: initscript dkms_autoinstaller, action "start" failed.
dpkg: error processing dkms (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

The troubling part is that it says the dkms package isn't fully installed or removed. I don't  know what to do about that.

---

### Post by taurus on 2007-12-26
Try the

```
sudo dpkg --configure -a
sudo apt-get update
```

---

### Post by fizikz on 2007-12-26
Here's what I get:

```
stephen@SSG1:~$ sudo dpkg --configure -a
Setting up dkms (2.0.17.5-0ubuntu1) ...
invoke-rc.d: initscript dkms_autoinstaller, action "start" failed.
dpkg: error processing dkms (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 dkms

```

The same error keeps showing up.

EDIT: In fact, any update using the automatic updates or synaptic package manager seems to fail with that the error: "E: dkms: subprocess post-installation script returned error exit status 1"

---

### Post by fizikz on 2007-12-27
I also tried using aptitude's interactive menu to either install or remove the dkms .deb package. Neither worked. Both times I get the failure error message. The dkms package is listed as not completely installed or removed. I'm running out of ideas here...

---

