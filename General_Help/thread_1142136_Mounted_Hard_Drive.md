---
title: "Mounted Hard Drive"
date: 2009-04-28
forum: General Help
---

### Post by fuzzybear3965 on 2009-04-28
Okay, so I have an internal hdd used exclusively for storage.  Three partitions, all in NTFS format.  I've tried to edit fstab to mount these drives but that changed the permissions.  I tried to edit these permissions using chmod (-R) on the mounted directory and the /dev/sdb* itself to no avail.  I even went so far as to remove the root group (keeping the root user).  Now, whenever I "ls -l /media/" what used to say 

drwxrwxrwx 1 root    root  40K 2009-04-27 21:42 Other
drwxrwxrwx 1 root    0  40K 2009-04-27 21:42 Other

chmod, chown, ch-anything is not working.  Not changing device permissions and I've since removed the entries from fstab.  Nothing!!!! Any help?

Oh, the problem.  No programs (deluge) can write to these directories.

---

### Post by Zimmer on 2009-05-02
Not an expert,  I use a gnome applet to mount my Windows partition so I do not see the commands ! but was curious.
This led me to 
[http://ntfs-3g.org/manual.html](http://ntfs-3g.org/manual.html)
and
[http://www.mkssoftware.com/docs/man1/chmod.1.asp](http://www.mkssoftware.com/docs/man1/chmod.1.asp)
which has some info on chmod and NTFS (not clear whether that is cross platform use to this particular passer-by )

Suggestion:
Install gnome-applets  and right click on the gnome panel , click on add and find DISK MOUNTER.
this will display icons for your partitions on the panel and you can click on the icons to mount the drive (no arcane commands required :) )
See if the drives mount and are accessible...

I cannot help if chmod has 'corrupted' the permissions and DISK MOUNTER will still not give you access.
I am hoping that the second link above may help if that turns out to be the case...
and that the first link will give you the info you need if you want to put the drives in fstab..
Regards
Zimmer

---

### Post by geirha on 2009-05-02
Here's a sample fstab line.
```
UUID=0123456789abcdef /media/storage1 ntfs-3g defaults,uid=*username*,gid=*groupname*,dmask=002,fmask=113 0 0
```
It mounts the ntfs filesystem with UUID 0123456789abcdef to /media/storage1

uid=*username* sets *username* as owner of all files and directories
gid=*groupname* sets *groupname* as group owner of all files and directories
dmask=002 gives everyone read and execute access to directories and write access to *username* and all members of the group *groupname*.
fmask=113 gives everyone read access to files and write access to owners, as with dmask.

---

