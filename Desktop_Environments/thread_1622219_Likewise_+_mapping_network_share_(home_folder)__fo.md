---
title: "Likewise + mapping network share (home folder)  for domain users ?"
date: 2010-11-15
forum: Desktop Environments
---

### Post by chrisdee on 2010-11-15
Hi.

I'v just installed Ubuntu 10.04 and likewise. I'v successfully enrolled the machine into the windows AD domain with likewise. Login with domain users works just fine:)

I also manage to manually map network shares / home folder when I login with my domain user.

However, I wonder if anybody can tell me how to automatically map network share (home shares) for all domain users loging onto the system ?

I have the paths to the shares, but don't know how to automate this. Help apreciated.

---

### Post by chrisdee on 2011-04-27
Bump.

I'm now running a Ubuntu 10.10 image via vmware player. I'v installed Likewise-Open 6.0. I manage to enroll the machines to the ad domain, but still no luck in automatically mapping network shares and home directories.

Any suggestions ?

---

### Post by cutekazuya on 2011-04-27
hello,

I have not tried auto mapping home directories but for network shares you can edit **/etc/fstab** and add something like 
```


//server/share    /mnt/dir   smbfs   username=user,password=xxx  0 0
```What i have personally done is when you open a network share, a shortcut to it appears on the desktop. Open Nautilus window and drag this shortcut under "places". OR in nautilus go to Bookmark > Add Bookmark when you have opened the network share.

From now on you will have shortcut to that share on any nautilus window and also at the top near applications > Places Menu

---

