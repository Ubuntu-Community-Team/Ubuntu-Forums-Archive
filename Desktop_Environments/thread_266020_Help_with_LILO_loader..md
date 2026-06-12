---
title: "Help with LILO loader."
date: 2006-09-26
forum: Desktop Environments
---

### Post by AT-AT on 2006-09-26
When I installed Ubuntu ([COLOR=gray]ubuntu-6.06.1-alternate-i386.iso[/COLOR] version; on an old computer 350 mhz, 384 MB ram, Windows 98 ) for some reason GRUB couldnt install, so I had to install LILO. I havent wanted to load Windows until now. How do I go about loading windows instead of Ubuntu? Thanks for the help.

---

### Post by AT-AT on 2006-09-26
Im not sure if its appropriate to bump this or not, but I'll do it anyway. Also, I forgot to say that Im dual booting.

---

### Post by kerry_s on 2006-09-26
What file system did you use?
there should be a example in your /etc/lilo.conf of a windows setup.Something like this->

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


Then you have to run in terminal> lilo

---

### Post by AT-AT on 2006-09-26
Lets see. Windows is in FAT32, Ubuntu is in ext3.
 
EDIT: Intresting, it posted this message even though I didnt hit reply.
 
Anyway, I've at least found out I need to edit LILO's conf file, and this is the part I need to edit.
 
[SIZE=2]# If you have another OS on this machine to boot, you can uncomment the[/SIZE]
[SIZE=2]# following lines, changing the device name on the `other' line to[/SIZE]
[SIZE=2]# where your other OS' partition is.[/SIZE]
[SIZE=2]#[/SIZE]
[SIZE=2]# other=/dev/hda4[/SIZE]
[SIZE=2]# label=HURD[/SIZE]
[SIZE=2]# restricted[/SIZE]
[SIZE=2]# alias=3[/SIZE]
[SIZE=2]other=/dev/hda1[/SIZE]
[SIZE=2]label=Windows9xMe[/SIZE]
[SIZE=2]# restricted[/SIZE]
[SIZE=2]# alias=2[/SIZE]
 
[SIZE=2]Im not entirely sure what I need to do, and even then I forgot how to log in as the user that can edit system files (ie, how to get full permissions). :embarassed: There's got to be a dummies guide, right?[/SIZE]

---

### Post by AT-AT on 2006-09-26
Im afraid to bump this again (I know some sites dont like repeated bumps), but I meant to make the information in the above post after the last edit as a seperate post. Its seems computers dont like me today, sorry.

---

### Post by AT-AT on 2006-09-27
Bump. I really could use some help, I cant find what I need to do through an internet search.

---

### Post by AT-AT on 2006-09-27
Ok, I think I know what the problem is now. Since LILO overwrote the master boot record, there is no program to boot windows on the hardrive. So does anybody have the files for a bootable floppy? It would be much appreciated.

---

