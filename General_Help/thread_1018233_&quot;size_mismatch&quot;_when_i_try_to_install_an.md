---
title: "&quot;size mismatch&quot; when i try to install any package"
date: 2008-12-21
forum: General Help
---

### Post by pencilbox889 on 2008-12-21
W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/pool/main/libg/libgpod/libgpod-common_0.6.0-3ubuntu3_i386.deb](http://archive.ubuntu-rocks.org/ubuntu/pool/main/libg/libgpod/libgpod-common_0.6.0-3ubuntu3_i386.deb)
  Size mismatch
I was atempting to follow these directions to sync my ipod touch:
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

when i tried to install ipod-convenience this happened:




W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/pool/main/libg/libgpod/libgpod3_0.6.0-3ubuntu3_i386.deb](http://archive.ubuntu-rocks.org/ubuntu/pool/main/libg/libgpod/libgpod3_0.6.0-3ubuntu3_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/pool/universe/s/sshfs-fuse/sshfs_1.9-1_i386.deb](http://archive.ubuntu-rocks.org/ubuntu/pool/universe/s/sshfs-fuse/sshfs_1.9-1_i386.deb)
  Size mismatch


W: Failed to fetch [http://archive.ubuntu-rocks.org/ubuntu/pool/universe/i/ipod-convenience/ipod-convenience_0.9-0ubuntu1_all.deb](http://archive.ubuntu-rocks.org/ubuntu/pool/universe/i/ipod-convenience/ipod-convenience_0.9-0ubuntu1_all.deb)
  Size mismatch


i tried to install some other packages and it seems to be doing that for everything


I am new to ubuntu and absolutely love it but know nothing about programing whatsoever. my ex installed ubuntu a while back and ive been able to do everything i wanted up to this point blindly using google. 

It turns out I wont be able to sync my ipod anyway because i have the new firmware but any help i could get to fix whatever i did to my poor computer would be apreciated.

thank you! ^^

---

### Post by orlox on 2008-12-21
Update manager doesn't show a messege that goes with that one. For instance, I found this on a bug report on launchpad:

```

Failed to fetch http://software.jessies.org/debian/./org.jessies.evergreen.deb Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

So I would reccomend you to use the following comands on a console:

```

sudo apt-get update --fix-missing
sudo apt-get install ipod-convenience --fix-missing

```

dunno if ti will work, never happened to me, but this is what i found...

hope it helps you

---

