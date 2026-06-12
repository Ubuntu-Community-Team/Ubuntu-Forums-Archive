---
title: "Gnome &quot;Computer&quot;"
date: 2005-08-13
forum: Desktop Environments
---

### Post by marcb on 2005-08-13
Hello,

I am quite new to Linux and I followed the steps in order to mount NTFS drives automatically from [www.ubuntuguide.org](www.ubuntuguide.org) and everything works OK. But I expect to see my mounted NTFS partition in Gnome's "Computer" window, but there is only "Floppy", "CD/DVD" and "Filesystem".
I have two questions, if someone could help me:
- How can I add my NTFS partition (I can access it via /media/windows) to "Computer"?
- I'm on a laptop with no floppy disk drive. Why it is showed on "Computer"? How can I remove it?

Thank you very much, any help is appreciated  ;-)

---

### Post by fresco on 2005-08-13
Hi there!

To remove floppy icon from Computer:
$sudo gedit /etc/fstab
comment the following line:

/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

So, after commenting it will look as follows:

#/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Save the file

Then,

$sudo mount -a

I should think about your first question.
Does anyone have any ideas?  :)

---

### Post by SuperMike on 2005-08-13
[QUOTE=marcb]Hello,

I am quite new to Linux and I followed the steps in order to mount NTFS drives automatically from [www.ubuntuguide.org](www.ubuntuguide.org) and everything works OK. But I expect to see my mounted NTFS partition in Gnome's "Computer" window, but there is only "Floppy", "CD/DVD" and "Filesystem".
I have two questions, if someone could help me:
- How can I add my NTFS partition (I can access it via /media/windows) to "Computer"?
- I'm on a laptop with no floppy disk drive. Why it is showed on "Computer"? How can I remove it?

Thank you very much, any help is appreciated  ;-)[/QUOTE]
 Sorry, but I would reason to bet that this is hard-coded. I peered in the settings app -- gconf-editor -- to see if I could find anything for you, but I could not.

If anything, it might pull whatever is in your /media folder on your Linux (EXT3) filesystem. You can create a new folder there, then use mount commands to mount your filesystem as this new folder.

I'm a little busy right now to give you the exact commands for mounting your NTFS in read-write mode, so I hope someone else shares that. The process, however, would be like:

mkdir /media/windows
mount -t ntfs /dev/<hd?> /media/windows

I don't know if the -t (type) option is correct for NTFS, but it might be. There's also a flag you need to turn on for read/write mode. (BTW, I've been told previously that read/write mode is experimental still, although many people have been successful with it.) As for what to put for /dev/<hd?>, perhaps someone can help you poll your system to determine where the NTFS drives are hiding. For instance, on my laptop where I have it set to dual boot, my NTFS drive was sitting at /dev/hdb1, I think. (Unfortunately I don't have my laptop with me right now to confirm that exactly.)

Last, to get this to work on reboot, you would edit /etc/fstab. The instructions for that are on the net. 

Otherwise, if you can't get fstab working, you have to put your mount command in some sort of startup script such as near the top of:

/etc/X11/gdm/Init/Default

or copy /etc/init.d/skeleton as /etc/init.d/mystartup, then edit it per the sysv daemon init script documentation on the net (Google for it).

---

### Post by varunus on 2005-08-13
Add this line to your fstab to mount your ntfs partition:
```
/dev/hd**       /media/windows  ntfs    nls=utf8,umask=0222 0       0
```

More information on mounting windows drives here:
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows)

If you don't know which /dev/hd** your windows partition is, that site has information on how to list partitions.

If you want it to show up in your "Computer" icon, you have to do something else with the fstab entry; let me look it up, then i'll edit this post.

EDIT:  Figured it out.  If you want the drive to show up in your computer place, make the fstab line the following:
```
/dev/hd**       /media/windows  ntfs    user,nls=utf8,umask=0222 0       0
```

---

### Post by marcb on 2005-08-13
Thank you guys! Your solutions worked perfectly :-)

SuperMike, don't worry about writing NTFS, i just needed reading the partition, I read NTFS support is experimental and writing is quite dangerous, and I just want to share my Windows files with Linux, I don't need to edit them.

One more thing that has come to my mind: now my Windows share appears in "Computer", its icon says "32G Hard Drive: 32G Media". This is purely cosmetic, but is there any way to rename this? (e.g. to "Windows Drive" or "Windows Filesystem")

Thank you again for your fast and efficient reply. You rock! ;-)

---

