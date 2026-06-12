---
title: "Restoring GNOME"
date: 2006-12-18
forum: Desktop Environments
---

### Post by lakelovers on 2006-12-18
This is probably a stupid question by then I'm not too swift at file knowledge. While messing around trying to fix my lost audio I inadvertantly messed up my GNOME desktop. I have backups of all my files but I don't know which files I need to restore to get GNOME back to normal. I have GNOME up but there's a couple of gliches. It nethier shuts down or loads correctly. Then I go to Sytem/Quite, only part of the "quite" screen shows. Missing is "Shutdown"  and I think one other option. When I start up I get some weird screen stuff but it does open into kbuntu where I can select ubuntu to load. So, what files do I need to restore or how do I otherwise get GNOME back to normal.
Jerry

---

### Post by taurus on 2006-12-18
Maybe reinstalling Gnome over again!!!

Applications -> Accessories -> Terminal
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

---

### Post by lakelovers on 2006-12-18
I should of listened the first time. I did the aptitude update and install unbutu-desktop. All went well except for this error message:

E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up alsa-base (1.0.10-4ubuntu4) ...
rm: cannot remove `/etc/modutils/alsa': Is a directory
dpkg: error processing alsa-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 alsa-base

This seems to be the problem I've been having trying to get my audio working.
What do you suggest?

---

### Post by taurus on 2006-12-18
What happens if you run

```
sudo aptitude remove alsa-base
sudo aptitude install alsa-base
```

---

### Post by lakelovers on 2006-12-18
I got this message when remvoing alsa-base: "This aptitude does not have Super Cow Powers." I also tried aptitude install alsa-base and got this:

$ sudo aptitude install alsa-base
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages have been kept back:
  totem
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Setting up alsa-base (1.0.10-4ubuntu4) ...
rm: cannot remove `/etc/modutils/alsa': Is a directory
dpkg: error processing alsa-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 alsa-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up alsa-base (1.0.10-4ubuntu4) ...
rm: cannot remove `/etc/modutils/alsa': Is a directory
dpkg: error processing alsa-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 alsa-base

---

### Post by taurus on 2006-12-18
Maybe you have to remove the /etc/modutils/alsa by hand first!!!

```
sudo rm -rf /etc/modutils/alsa
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by lakelovers on 2006-12-18
Here's what I got 

The following packages have been kept back:
  totem
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up alsa-base (1.0.10-4ubuntu4)

---

### Post by taurus on 2006-12-18
Did you remove the "/etc/modutils/alsa" directory first?

```
ls -la /etc/modutils
```

---

### Post by lakelovers on 2006-12-18
I am inching along. The last code returned this:ls -la /etc/modutils
total 32
drwxr-xr-x   2 root root 4096 2006-12-18 12:10 .
drwxr-xr-x 130 root root 8192 2006-12-18 11:40 ..
-rw-r--r--   1 root root   97 2005-04-15 03:41 apm
-rw-r--r--   1 root root  233 2005-10-03 04:12 bluez
-rw-r--r--   1 root root   29 2005-07-21 21:19 evms
-rw-r--r--   1 root root  121 2000-12-26 15:58 lvm-common
-rw-r--r--   1 root root   28 2005-07-26 10:23 nvidia-kernel-nkc

---

### Post by taurus on 2006-12-18
Okay, directory alsa is gone.  Now, what happens if you run these two commands?

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by lakelovers on 2006-12-18
Both commands executed okay with the second command ending with:

The following packages have been kept back:
  totem
0 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

---

