---
title: "Nautilus Partition/Directory name severe problem"
date: 2008-05-26
forum: Desktop Environments
---

### Post by lngndvs on 2008-05-26
This I need to solve at once, or perhaps get away from this distro.  

I have the following in my /etc/fstab:

[INDENT]# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda8
UUID=b24c270c-445d-4843-8dc6-b5dcc22195e7 /               ext3    errors=remount-ro 0       1
# /dev/sda1
UUID=af948971-8091-4105-85f0-c471ab886fc8 /home           ext3    defaults        0       2
# /dev/hda1
#UUID=bdf22285-b001-4780-8e68-a000e2df8eb9 /media/hda1     ext2    defaults        0       2
# /dev/hda2
UUID=b652dea8-5619-40ae-ae48-d6d3ced98264 /media/hda2     ext3    defaults        0       2
# /dev/hda3
#UUID=5433ff4c-9841-47ae-b5a0-e71cc30f33f3 /media/hda3     ext3    defaults        0       2
# /dev/hda6
UUID=f6175525-5ff4-44e7-ab35-9bac7ae7ec2a /media/hda6     ext3    defaults        0       2
# /dev/hda7
UUID=c7a3c324-b660-4acc-8ace-d59cef7bdc8b /media/hda7     ext3    defaults        0       2
# /dev/sda2
UUID=8823e2d6-e44b-478f-a54d-c59887ef9637  /home/aed/ANYTHING   ext3    defaults        0       2
# /dev/sda5
UUID=00b7db1e-109d-4787-9abf-fc114d341566   /home/aed/Videos/VIDEO3     ext3    defaults        0       2
# /dev/sda6[/INDENT]

When I am using Nautilus only, in the Home folder (/home/aed/) and click on ANYTHING folder, the folder is displayed as /home/aed/video2.

More explanation:

I have just gotten used to the Places menu, and I use the sidebar of Nautilus to drag important directories to that sidebar, so I can access them instantly.  Very nice feature, I now like Gnome better than anything else, because of the convenience and ease...   However, I am afraid to reorganize the directory structure of my HDDs, because I cannot know what is correctly what!  

I am peeved about the use of identifiers in the sidebar for partitions and directories that I am unfamiliar with.  Instead of a directory name or a /dev/XXX I have identifiers that are useless to me:

    493.5 MB media
    26.5 GB Media
    9.3 GB Media
    video3
    video4
    video2
    1.0 GB media

I have gotten used to the 1.0 GB media being my flash drive.  I don't know rightly what video3, video4, and video2 are, but I have similarly named partitions in certain places.  

Thunar doesn't show any of this gibberish.  It does show the Places I have dragged into the sidebar of nautilus, and that are in the Places menu under Bookmarks (I'd rather have them outside that folder and clearly visible, but it works ok).

This has to be solved.  Maybe I can drag them out of the Places?

Thank you for any help on this.  I am crazy about the Hardy Heron; I'd be bummed to go back and start from scratch wtih something else.  

Alan :confused:

---

### Post by hamiltonlight on 2008-05-29
Hello,

I upgraded to 8.04 last night and have just found the same thing. Currently cannot find where I can change this behavior. Its frustrating as it was logical before and seems a step backwards on a new version of the OS. 

I've currently assigned a custom icon to each mount point until I find a fix. 

Regards

---

