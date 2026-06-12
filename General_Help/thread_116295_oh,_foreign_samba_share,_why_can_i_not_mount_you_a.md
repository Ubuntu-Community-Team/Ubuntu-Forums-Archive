---
title: "oh, foreign samba share, why can i not mount you as user from a desktop launcher?"
date: 2006-01-12
forum: General Help
---

### Post by lapsey on 2006-01-12
I've been trying to mount samba shares to the filesystem ever since I realised that gnome's method of handling samba means most linux applications wont have access to them.

because I don't always have access to the shares, I have been trying to mount them to a local folder via a desktop launcher (rather than via fstab or one of the many unusable graphical share browers for linux)


something like:

> gksudo -u root "mount -t smbfs //ixion/public /home/me/Desktop/public -o username=public,password=public,fmask=755,dmask=755,rw"

only problem is i find i only have read-access to the folder. i suspect this is because mount is only mountable by root, yet I can't give

the parameters seem all above board, and nautilus can access the share via smb:// with full read-write permissions, so there seems to be nothing wrong on the server side.

I am confused.



-----------------------------------


FIXED thanks to help of the kind people in irc.freenode.org/samba

"mkdir Desktop/public ; smbmount //ixion/public /home/me/Desktop/public -o username=public,password=public,fmask=755,dmask=755,rw"

---

### Post by Robor on 2006-01-12
I've been trying to mount a remote share (Win2003 Server) from my Ubuntu laptop and failed miserably.  I'm sure it's a PICNIC error rather than something with Ubuntu but given that I'm in the same situation as you I hope someone can help with a solution.

---

