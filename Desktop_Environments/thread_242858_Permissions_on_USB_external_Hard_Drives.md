---
title: "Permissions on USB external Hard Drives"
date: 2006-08-24
forum: Desktop Environments
---

### Post by The Pinny Parlour on 2006-08-24
Hi all,

Got an external hard drive connected via USB.  Drive is FAT32, it shows up in ubuntu but I cannot write to it.  Any ideas how to get access to it?

TIA.

---

### Post by michux on 2006-08-24
> **The Pinny Parlour said:**
> Hi all,

Got a external hard drive connected via USB.  It in FAT32, it shows up in ubuntu but I cannot write to it.  Any ideas how to get access to it?

TIA.

Do it manually. You can try this advice: [How to mount a pendrive (USB stick)](http://polishlinux.org/first-steps/filesystem-and-disks/#disk_pendrive)

---

### Post by The Pinny Parlour on 2006-08-24
Thanks but I'm not sure that is for my situation.  My disk shows as a storage device etc,  I want to write files to it but can't.  

This is the access path: /tmp/disks-conf-sdc1 

I can't write to it.

Error while copying to "/tmp/disks-conf-sdc1".  You do not have permissions to write to this folder.

Any other ideas?  

Cheers

---

### Post by carontis on 2006-08-24
I think you have to give permissions to the drive for writing and surely you'll have to do it as superuser (sudo su). Anyway it looks strange to me 'cause I tried an external drive USB and it was seen quikly and without problems. The only problem was like yours: I wasn't able to write in it 'cause of permissions, but logged as superuser I was able to everything. Try see if it helps a little (hope so).
bye

---

### Post by The Pinny Parlour on 2006-08-24
> **carontis said:**
> I think you have to give permissions to the drive for writing and surely you'll have to do it as superuser (sudo su). Anyway it looks strange to me 'cause I tried an external drive USB and it was seen quikly and without problems. The only problem was like yours: I wasn't able to write in it 'cause of permissions, but logged as superuser I was able to everything. Try see if it helps a little (hope so).
bye

Thank you for your reply.  Could you give me an idea of how one would perform that task please?

Thank you.

---

### Post by The Pinny Parlour on 2006-08-24
Bump

---

### Post by suchawato on 2007-11-03
First of all, 
be aware that you might run into the [Gparted bug]("https://bugs.launchpad.net/ubuntu/+source/gparted/+bug/134712").
But if you don't, here is how you change the permissions:
in a terminal type
```
gksudo nautilus
```
enter your password at the prompt.
now double-click on the filesystem icon on the left.
Open up "Media".
Right click on the folder that is your drive.
Select properties.
One of the tabs, will lit you change the owner, and permissions from root, to Nobody or whomever.
Change the permissions the way you like.
click "apply changes to subfulders"(or somthing like that)
exit out and leave sudo nautilus.
You should be done!

By the way, is it a LaCie external harddrive?

---

