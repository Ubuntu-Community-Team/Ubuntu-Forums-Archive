---
title: "usbdisk for all users"
date: 2005-07-19
forum: Desktop Environments
---

### Post by MatthewMetzger on 2005-07-19
Hello,

I just got a usb pen drive for a person in my office. Our office computers have several users that share the computer. My user (the one that was set up during the ubuntu install) mounts and uses the usbdisk fine, but other users cannot. I granted each of these users full privileges in the Users and Groups part of the Administration section.

It works fine in my user, but when I try to mount the disk as another user it tells me that the current user does not have sufficient privileges.

Any thoughts on how I can get the new usb drive to work for all users?

thanks much for any help you can give me.

Matthew Metzger

---

### Post by professor_chaos on 2005-07-19
What does the ownership/permission report on the device

```
ls -l /media/
```

---

### Post by MatthewMetzger on 2005-07-19
Here's the result:

drwx------  2 amy  amy  28160 1969-12-31 18:00 usbdisk

I think what is happening is that I'm using gdmflexiserver to switch between more than one user at a time. The usb pen drive is not necessarily mounted with the user that I'm currently viewing, but with whatever user seems to get to it first. Once it is mounted by one user, the other users cannot read or write to it.

How do I get it to be used by all users? Even when multiple users are logged in at the same time? (we do this so that people who are working on a project don't have to log out if someone else needs to use the computer for a while).

I look forward to your response.

---

### Post by professor_chaos on 2005-07-19
I don't really seem to have an answer here. I am too a bit stumped.
Try as I might, I can't seem to mount my flash drive with group permissions.

I googled a bit, and read suggestions about formating to ext3 instead of fat32, as fat32 doesn't handle premissions appropriately. I personally need mine as fat, as its used in M$ machines. Sorry I can't be of more help. ](*,)  ](*,)  ](*,)

---

### Post by MatthewMetzger on 2005-07-19
Thanks for trying to help Professor Chaos. If I figure out a solution, I'll post it for everyone's benefit. If anyone else has any ideas on how I can use one usb pen drive for multiple users loggin in at the same time, I'd love to hear them.

Thanks,

Matthew

---

### Post by Joeb on 2005-07-19
[QUOTE=MatthewMetzger]Thanks for trying to help Professor Chaos. If I figure out a solution, I'll post it for everyone's benefit. If anyone else has any ideas on how I can use one usb pen drive for multiple users loggin in at the same time, I'd love to hear them.

Thanks,

Matthew[/QUOTE]


What does your /etc/fstab look like?

Joeb

---

### Post by MatthewMetzger on 2005-07-19
[QUOTE=Joeb]What does your /etc/fstab look like?

Joeb[/QUOTE]
 # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

### Post by MatthewMetzger on 2005-07-20
It looks like this is an area in Ubuntu that might need to be refined. I emailed Mike at groovix.com (maker of multiuser linux systems). He said that they have full automated scripts for handling the sharing of usbdisks on Debian w/KDE, but that a similar sharing has not been worked out for their Ubuntu systems.

Groovix's scripts can be downloaded from [http://groovix.com/linuxconsole.html](http://groovix.com/linuxconsole.html)

I hope this helps some people. I am resorting to telling the people in the office that only one person can be logged in if they want to use a usbdisk. Bummer, but workable.

---

### Post by MatthewMetzger on 2005-07-20
[QUOTE=MatthewMetzger]He said that they have full automated scripts for handling the sharing of usbdisks on Debian w/KDE, but that a similar sharing has not been worked out for their Ubuntu systems.[/QUOTE]

I want to clarify that they (groovix) do have a way of handling the usbdisk for multiple users in ubuntu that is quite ingenious. It just wouldn't exactly work as I want it to for my situation.

If we had a bigger budget, I'd definately consider buying a Groovix multiuser system for our afterschool program.

---

### Post by olafbooij on 2005-10-05
Hi all,

I ran into the same problem. I am using gdmflexiserver, so my wife and I can be logged in at the same time. 
When I plug in my usb-memory-stick, camera with usb-cable or insert a dvd or floppy the result is that the owner is (apparently) randomly chosen among the users who are logged in.
The problem is that only the owner can unmount the device.
In addition for the usb devices only the owner has read/write access.
I solved this with some (very) dirty fixes. (Sorry, I did not look at the Groovix scripts).
First I added a directory to the /media directory:

mkdir /media/usbsdb1

Then I added a line to my /etc/fstab regarding the usb-port /dev/sdb1 that I (and the other users) use for my devices:

/dev/sdb1       /media/usbsdb1  msdos   rw,user,users,noauto,umask=000  0       0

A you can see this is only for msdos filesystems which is good for me, because all usb-storage devices I use have this format. The "users" option causes the device to be unmount-able for all users. The "umask=000" option (which is only for msdos filesystems) causes the directory /media/usbsdb1 to be read-writable by everyone (I know: this is not very nice).
I also added the "users" option for my dvd and floppy-driver:

/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,users,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,users,noauto  0       0

making them unmountable by all users.

I know: this is not a solution to the problem, only a quick dirty fix to make my wife happy.

Olaf

---

