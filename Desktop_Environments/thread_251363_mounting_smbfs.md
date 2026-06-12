---
title: "mounting smbfs"
date: 2006-09-05
forum: Desktop Environments
---

### Post by madsporkmurderer on 2006-09-05
I am trying to mount a samba share perminantly to my file system as /music, I have tried adding the correct line to fstab. It should work as it was copied from another computer on the same network also running ubuntu 6.06 where it works trouble free.

the line is "//downstairs/Music /music smbfs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode 0 0"

the share is definately correct as it can be accessed by nautilus at smb://downstairs/music

---

### Post by f00buntu on 2006-09-05
Did you install smbfs already?

sudo apt-get install smbfs

---

### Post by kuja on 2006-09-05
If you've got smbfs installed. What is the codepage=unicode,uni code" part doing... maybe it doesn't agree with the space?

Also, you could try mounting with the mount command manually...
If it doesn't work, simplify it, and then gradually add on options until you get to your full mount -t smbfs -o uid=1000 -o iocharset=utf8 -o codepage=unicode //downstairs/music /music or what not.

---

### Post by madsporkmurderer on 2006-09-05
Thanks a lot, you guys are really great, I realised erlier that I didn't even include the error message and expected to get a bad response(fairly so) but in fact you have solved the problem.

It was that I didn't have smbfs installed- always the simple things that cause the big problems

---

