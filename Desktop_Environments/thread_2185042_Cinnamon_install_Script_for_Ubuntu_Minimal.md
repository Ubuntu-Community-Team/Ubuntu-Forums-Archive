---
title: "Cinnamon install Script for Ubuntu Minimal"
date: 2013-10-31
forum: Desktop Environments
---

### Post by quids on 2013-10-31
Hi Guys & Girls
I've created a bash script to get a basic Cinnamon desktop functioning from Ubuntu Minimal.

[http://paste.debian.net/63208/](http://paste.debian.net/63208/)

```

wget http://paste.debian.net/download/63208
bash 63208
```

I've only been able to try it out in Ubuntu 13.10 Server in Virtualbox and on an Nvidia based system.
Personally I would have gone with Snow Linux for simplicity, but I expect there might be a fair few people who would find this script useful.

Known Issues
 
[LIST]
[*]Some of the right-click menus don't open their assigned system control app 
[*]AMD Graphics driver installer is completely untested 
[/LIST]
 
I don't think Ubuntu Minimal ISO works with UEFI Secure Boot, so you'll have to use Ubuntu Server instead
Ubuntu Minimal: [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)
Ubuntu Server: [http://www.ubuntu.com/download/server](http://www.ubuntu.com/download/server)

---

### Post by ian-weisser on 2013-10-31
I see that the script seems to use a PPA (unsupported) version of Cinnamon instead of the (supported) Ubuntu Repository version.
Reason?

---

### Post by vasa1 on 2013-10-31
> **ian-weisser said:**
> I see that the script seems to use a PPA (unsupported) version of Cinnamon instead of the (supported) Ubuntu Repository version.
Reason?
Check out [http://ubuntuforums.org/showthread.php?t=2184396](http://ubuntuforums.org/showthread.php?t=2184396). I get the impression that the PPA is less outdated than the repo version.

---

