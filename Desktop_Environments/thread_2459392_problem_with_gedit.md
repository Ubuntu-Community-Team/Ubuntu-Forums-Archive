---
title: "problem with gedit"
date: 2021-03-17
forum: Desktop Environments
---

### Post by thumper76 on 2021-03-17
Every time run gedit as SUDO from the command prompt I get this error message when I close it:

(gedit:3903): Tepl-WARNING **: 18:12:42.100: GVfs metadata is not supported. Fallback to TeplMetadataManager. Either GVfs is not correctly installed or GVfs metadata are not supported on this platform. In the latter case, you should configure Tepl with --disable-gvfs-metadata.

Any suggestions what to do about this?

---

### Post by CatKiller on 2021-03-17
Don't run gedit with sudo.

---

### Post by DuckHook on 2021-03-17
> **CatKiller said:**
> Don't run gedit with sudo.
&#8593; +1 &#8593;

In fact, do not run ***ANY*** GUI app with sudo.

---

### Post by Frogs Hair on 2021-03-17
To avoid  permissions problems caused by running gui applications with sudo try the following ```
pkexec gedit 
``` or```
 sudo -H gedit
```

---

### Post by CatKiller on 2021-03-17
The very neat option is to use sudoedit: you can specify which editor you want to use if it's not the default.

It does the sensible thing of copying whatever file to /tmp, then editing *that* with your editor as your unprivileged user, so that you don't muck up your own files in your Home directory, and so that you aren't running a bunch of GUI libraries as root, and then copies it back when you're done. The only part that requires root privileges is the final copy. Doing the rest as root is bad security and runs the risk of going Terribly Wrong.

---

### Post by DuckHook on 2021-03-17
A further option is to install the nautilus-admin package which not only gives the option of safely opening system files with gedit as root, but also manipulate them with nautilus as root. All in all, CatKiller's recommendation is the safest, for all the reasons he has already stated.

---

### Post by thumper76 on 2021-03-18
If you don't use sudo you can't edit the file. It's read only.

---

### Post by thumper76 on 2021-03-18
Using -H get rid of the error message. I do remember now that all GUIs run from the terminal should use -H. But I guess it's better to use nano.

---

### Post by Morbius1 on 2021-03-18
I would ignore the error message. It seems to be a bug in gedit. It doesn't happen if you use another editor ..... like mousepad for example:
> tester@vub2004:~$ sudo gedit /etc/fstab
[sudo] password for tester: 

(gedit:3137): Tepl-WARNING **: 07:11:27.981: GVfs metadata is not supported. Fallback to TeplMetadataManager. Either GVfs is not correctly installed or GVfs metadata are not supported on this platform. In the latter case, you should configure Tepl with --disable-gvfs-metadata.
tester@vub2004:~$ sudo mousepad /etc/fstab
tester@vub2004:~$ 

BTW, Ubuntu changed how sudo works back in 19.10. It now works the way it does on all other distros: [https://askubuntu.com/questions/1186999/how-does-sudo-handle-home-differently-since-19-10](https://askubuntu.com/questions/1186999/how-does-sudo-handle-home-differently-since-19-10)

> For years, Ubuntu has [shipped a patched version of sudo that preserves $HOME by default]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/760140"). Besides Ubuntu and its derivatives, [very few other operating systems (perhaps no others) do this]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/1556302/comments/8"). It has been [**decided that this causes more problems than it solves**]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/1556302"), and [starting in Ubuntu 19.10]("https://bugs.launchpad.net/ubuntu/+source/sudo/+bug/1556302/comments/16"), $HOME is no longer one of the few environment variables sudo preserves.

---

### Post by ActionParsnip on 2021-03-18
Could just use vi and embrace the dark side :)

---

