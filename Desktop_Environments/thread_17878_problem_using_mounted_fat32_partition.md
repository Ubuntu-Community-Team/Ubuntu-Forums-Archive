---
title: "problem using mounted fat32 partition"
date: 2005-03-03
forum: Desktop Environments
---

### Post by lorap on 2005-03-03
after i mount fat32 this way:
sudo mount -t vfat /dev/hda1 /home/lorap/c
i can see what's on that partition but cannot open folders and make any other changes.
if somebody know how to solve this problem, then help me please.
pavel

---

### Post by bored2k on 2005-03-03
[QUOTE=lorap]after i mount fat32 this way:
sudo mount -t vfat /dev/hda1 /home/lorap/c
i can see what's on that partition but cannot open folders and make any other changes.
if somebody know how to solve this problem, then help me please.
pavel[/QUOTE]

looks lik ur mounting readonly dude

i use this to mount my fat 32 flawlessly

> sudo mount /dev/hda1 /home/lorap/c -t vfat -o umask=000 


id recmmend making a script that does this automatically, this would be making a "mount.sh" text with this inside :
> 
#!/bin/sh
sudo mount /dev/hda1 /home/lorap/c -t vfat -o umask=000 

then giving it chmod 755 permissions , and opening it with ./mount.sh or sh mount.sh

---

### Post by lorap on 2005-03-03
Thank you very much Friend for the help hand you've given me.
Pavel.

---

### Post by bored2k on 2005-03-03
[QUOTE=lorap]Thank you very much Friend for the help hand you've given me.
Pavel.[/QUOTE]


np dude.

For better documentation, be sure to check out Chua Wen Kiat's flawless [Unofficial Ubuntu Guide (Mounting Section)](http://ubuntuguide.org/#windows) <-- there are some loose ends on that guide [like compiling java, wich can be done adding some ubuntu sources] , but that windows part "est parfait"  .

---

