---
title: "Mounting shares from another Linux box"
date: 2009-04-06
forum: General Help
---

### Post by DottM on 2009-04-06
Hi everyone, 

To give a little background I have a little server i run with slackware on it to serve my media and documents. I have recently got a new job since finishing university and all thier systems are linux based so i have decided to install ubuntu on my main machine and see if it will help me get to grips with things alot quicker.

So i have folders on my slackware server that im looking to mount on my main machine. i have my slackware box running on 10.0.0.25 and my ubuntu machine on 10.0.0.15

i have added the following to my fstab file 
> //10.0.0.25/scott    /home/scott/Documents smbfs  credentials=/root/.smbcredentials,dmask=0777,fmask=0777  0    0

now when i try to view the contents i get a permission denied. so if i sudo in on it i can view the files. 

I spoke briefly with a friend and he mentioned it something to do with the group id's on each machine as it was different flavours of linux they may well be different.. 

when i list my folder i have the following attributes for my documents folder

> drwx--x--x 25 scott    users 1184 2009-04-06 18:25 scott/


so i gather it is owned by the users group,

in the /etc/passwd file i have the following on my slackware box:
> scott:x:500:100::/home/scott:/bin/bash

and this on my ubuntu
> scott:x:1000:1000:Scott MacDonald,,,:/home/scott:/bin/bash

now i tried messing about with the group id's and ended up messing the computer up and having to boot from teh recovery disk. Can anyone shed some light or help on what i should do.

Im sorry for the masses of info just thought it would be best to offer too much than too little.

Thank you in advance

---

### Post by stchman on 2009-04-06
Use NFS or ssh instead of Samba.  Remeber Samba is a reverse engineered version of Windows SMB protocol.

I have a tutorial for NFS.

[http://www.stchman.com/share_NFS.html](http://www.stchman.com/share_NFS.html)

Hope this helps.

---

### Post by DottM on 2009-04-06
thanks for your advice stchman, but i still have a little netbook that i connect to with windows on it to share the same files. so changing it over i guess i would no longer be able to access these files on that?

---

### Post by stchman on 2009-04-06
> **DottM said:**
> thanks for your advice stchman, but i still have a little netbook that i connect to with windows on it to share the same files. so changing it over i guess i would no longer be able to access these files on that?

It has been my experience that Linux has problems connecting to Windows shares.

Samba was made for Windows machines to connect to Unix shares.

---

### Post by DottM on 2009-04-06
> **stchman said:**
> It has been my experience that Linux has problems connecting to Windows shares.

Samba was made for Windows machines to connect to Unix shares.

so is it just not possible to have linux mount a windows share? if i change the permissions on the slackware box to 770 i can then access it without prompt but i dont want to really do this as then any user on my slackware box can access this

---

### Post by stchman on 2009-04-06
> **DottM said:**
> so is it just not possible to have linux mount a windows share? if i change the permissions on the slackware box to 770 i can then access it without prompt but i dont want to really do this as then any user on my slackware box can access this

It is possible, just that in my experience the mount will be spotty at best.  NFS is a far more reliable option.

Why does one want to use a M$ proprietary protocol for Linux boxes to share files?

Creating NFS shares is way easier.

---

### Post by DottM on 2009-04-09
but if i was to use NFS would my windows laptop still be able to view the files and mount as a network drive?

---

