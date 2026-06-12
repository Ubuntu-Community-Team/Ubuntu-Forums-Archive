---
title: "Newbie questions"
date: 2005-11-08
forum: Desktop Environments
---

### Post by Lambic on 2005-11-08
Hi,
I installed Kubuntu 5.10 in a dual boot configuration with Win XP Pro on a machine with an Athlon 64 3200+, 1 GB RAM, two 120 GB hard drives-the IDE master has the Windows, the slave was formatted during installation for Kubuntu. I'm very happy with the experience so far, most of the important things worked right away (sound, printing, Internet,) and I find the environment much more, for the lack of a better word, pleasing. 
I have a few obviously newbie questions, tough, so here they are:
1. My scanner wasn't recognized by the included scanning application (forgot the name, I'm writing from a work PC now.) It's a CanoScan Lide 30. Do I need to find drivers for this thing? It's connected via USB, plugged into a hub.
2. I can't see the volume with Windows from Linux, and vice versa--that is the Linux drive became invisible in Windows, too. I'd like to be able to transfer files between those drives, how do I go about enabling that? Samba? 
3. Is there an easy way to port my Firefox settings from the Windows version to Linux? (Bookmarksm, I mean.) How about Outlook's mailboxes to Thunderbird?
I would appreciate if you guys could point me in the right direction for finding answers.
Thanks in advance.

---

### Post by Navyblue on 2005-11-08
[QUOTE=Lambic]1. My scanner wasn't recognized by the included scanning application (forgot the name, I'm writing from a work PC now.) It's a CanoScan Lide 30. Do I need to find drivers for this thing? It's connected via USB, plugged into a hub.[/QUOTE]

I know nuts about scanner, so I can't help you with this.

[QUOTE=Lambic]2. I can't see the volume with Windows from Linux, and vice versa--that is the Linux drive became invisible in Windows, too. I'd like to be able to transfer files between those drives, how do I go about enabling that? Samba?[/QUOTE]

Your windows drives are not mounted. To mount them you gotta add them in to /etc/fstab. You might want to show us your /etc/fstab and your hardware setup (which drive and partition).

[QUOTE=Lambic]3. Is there an easy way to port my Firefox settings from the Windows version to Linux? (Bookmarksm, I mean.) How about Outlook's mailboxes to Thunderbird?[/QUOTE]

I did not try to export my mail and bookmarks. So I didn't explore on this and sorry that I can't help you with it. I only exported my address book.

---

### Post by Adrian on 2005-11-08
This program lets you access your Linux (ext2/ext3) partitions from Windows:
[http://www.fs-driver.org/](http://www.fs-driver.org/)

I'm using it myself and it works very well.

---

### Post by mlomker on 2005-11-08
> 1. My scanner wasn't recognized by the included scanning application (forgot the name, I'm writing from a work PC now.) It's a CanoScan Lide 30. Do I need to find drivers for this thing? It's connected via USB, plugged into a hub.

I'd recommend a separate post for this in the hardware section if someone doesn't reply.  It doesn't really matter whether you are using kde or gnome for that.

> 2. I can't see the volume with Windows from Linux, and vice versa--that is the Linux drive became invisible in Windows, too. I'd like to be able to transfer files between those drives, how do I go about enabling that? Samba? 

Someone else posted the driver for the Windows side.  On the linux side you'd have to mount the partition.  [Read this.]("http://www.ubuntuguide.org/#windows")

> 3. Is there an easy way to port my Firefox settings from the Windows version to Linux? (Bookmarksm, I mean.) 

I'm not sure of an *easy* way, but I find a semi-difficult way.  :)

You need to copy your bookmarks.html file from Windows and then place it into the proper directory in Ubuntu.  It is under your home directory in an oddly named directory (yours will be different):

```

mlomker@mlomkernote:~/.mozilla/firefox/f6rtx3vi.default$ ls book*
bookmarks.bak  bookmarks.html

```

> How about Outlook's mailboxes to Thunderbird?

Perhaps you should install the Windows version first and see if it can be imported?  If it can then you can copy the proper files over like with Firefox.

---

### Post by f1dave on 2005-11-08
Thunderbird windows -> thunderbird linux is fairly easy to do, i've done it a number of times- simply a matter of copying some folders. However outlook is a different kettle of fish. Perhaps a google for "importing outlook mail thunderbird" or a search on the mozilla forums is in order?

---

### Post by aysiu on 2005-11-08
[QUOTE=f1dave]Thunderbird windows -> thunderbird linux is fairly easy to do, i've done it a number of times- simply a matter of copying some folders. However outlook is a different kettle of fish. Perhaps a google for "importing outlook mail thunderbird" or a search on the mozilla forums is in order?[/QUOTE] I would install Thunderbird on Windows. I believe it's set up to import from Outlook (I could be wrong). Once that import is done, it's easy to migrate that from Thunderbird Windows to Thunderbird Linux.

---

### Post by Lambic on 2005-11-09
Thank you all for your responses. 
Two out of my three problems solved on the first post--not bad...I wish I had a similar success ratio on match.com.
(Kidding, married old fart here...)
So, the scanner problem: it showed up in Kooka (btw, wtf with these names?) on reboot.
The Windows driver: works like a charm, thanks Adrian!
Mounting the Windows HD: I followed the instructions <a href="http://www.ubuntuguide.org/#windows">here,</a> and I got this message:
mount: wrong fs type, bad option, bad superblock on /dev/hda1,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by mlomker on 2005-11-10
If you post the output of these then we'll take a look:

```

sudo fdisk -l
cat /etc/fstab

```

---

### Post by Lambic on 2005-11-10
Thanks!
Here you go:
> Disk /dev/hda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       14592   117210208+   7  HPFS/NTFS

Disk /dev/hdb: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       14574   117065623+  83  Linux
/dev/hdb2           14575       14946     2988090    5  Extended
/dev/hdb5           14575       14946     2988058+  82  Linux swap / Solaris
lekics@ubuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hdb1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hdb5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hda1       /media/windows  vfat    iocharset=utf8,umask=000   0       01


---

### Post by mlomker on 2005-11-10
It looks like your Windows drive is NTFS and not VFAT.  Did you know that NTFS drives are read-only under Ubuntu?  There are tools to make them read/write but they aren't safe to use.

Try changing the line to

```

/dev/hda1 /media/windows ntfs nls=utf8,umask=0222 0 0

```

---

