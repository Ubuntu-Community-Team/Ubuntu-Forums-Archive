---
title: "Seeing my windows partition"
date: 2005-11-27
forum: Desktop Environments
---

### Post by Norred on 2005-11-27
Is there a reason why i cant see all of my windows files in Ubuntu??  I see my system files and stuff but i dont see program files... documents and settings and those kind of things.

---

### Post by quietglow on 2005-11-27
Have you followed the directions here? :

[http://ubuntuguide.org/#windows]("http://ubuntuguide.org/#windows")

---

### Post by Norred on 2005-12-16
Thx...   but it says they are already mounted, but nothing is in hda1...  there are some windows files in hda5 but not all of it...  like i need to go into mydocuments and program files but there are none..   im guessing that hda5 is my recovery archive for windows... and hda1 is the windows partition which nothing is there..  idk its confusing and i want to acess my windows stuff from linux.   I can do it on Mandriva Linux.. but not Ubuntu.

---

### Post by bonsiware on 2005-12-16
if you prefer graphic mode:

- create a new folder il \media\ (for example 'windows') 
- system --> administration --> disks
- select the hard drive and go in the partitions tab
- find the fat32 or ntfs one
- change access path to the above created folder
- press enable, then browse

I hope it will work in this way...

---

### Post by aysiu on 2005-12-16
See the fourth link of my sig.

---

### Post by Norred on 2005-12-18
[QUOTE=bonsiware]if you prefer graphic mode:

- create a new folder il \media\ (for example 'windows') 
- system --> administration --> disks
- select the hard drive and go in the partitions tab
- find the fat32 or ntfs one
- change access path to the above created folder
- press enable, then browse

I hope it will work in this way...[/QUOTE]


  Thankyou Bonsiware.... it worked.  Now I just need one more question..  Where do I install software packages??  for instance mandriva has a software installation program in  Configure Computer.   Where is the software installer on Ubuntu? I dont see any in the menu.

---

