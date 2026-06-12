---
title: "Another &quot;Edit Places&quot; post"
date: 2008-07-05
forum: Desktop Environments
---

### Post by Yoshis88 on 2008-07-05
Hey, first post here.  I've been poking with Ubuntu since 6.06, but ever since 8.04 came out, I've been quite happy with it and by default boot into it (disk space from Windows is slowly being re-siphoned :)

I'm very interested in how to remove specific partitions from appearing in the "Places Menu".  Note the attached picture.  I would like that partition in the red box to not be present.
[IMG]http://lh3.ggpht.com/Yoshis88/SG8oOqitNNI/AAAAAAAAAGc/vtmilyiFBhU/Screenshot.png[/IMG]

So, I tried to learn something by searching previous posts.
Somewhat relevant literature search:
[http://ubuntuforums.org/showthread.php?t=207021](http://ubuntuforums.org/showthread.php?t=207021)
[http://ubuntuforums.org/showthread.php?t=89136](http://ubuntuforums.org/showthread.php?t=89136)
[http://ubuntuforums.org/showthread.php?t=415287](http://ubuntuforums.org/showthread.php?t=415287)
[http://ubuntuforums.org/showthread.php?t=833958](http://ubuntuforums.org/showthread.php?t=833958)
[http://brainstorm.ubuntu.com/idea/2951/](http://brainstorm.ubuntu.com/idea/2951/)
[http://library.gnome.org/admin/system-admin-guide/stable/menustructure-0.html.en](http://library.gnome.org/admin/system-admin-guide/stable/menustructure-0.html.en)

Let it be known:
I'm no stranger to Ubuntu.  I'm not scared of the terminal :)  I am happy to post any files or outputs to commands.  I like exploring and learning how to use and configure computers.

What I've learned:
I do not want to prevent the mounting of these partitions, I just don't want that entry to be visible in the "Places" menu, so the mounter uses the terminal to mount the partition.  pysdm is a cute frontend to edit the fstab, but I don't think this is an fstab problem.  This is an issue of GNOME providing an entry I wish to delete.

Bookmarks are editable with a file I found as well as the Nautilus GUI.  Bookmarks are the entries above the first divider.  Unfortunately, the focus of the problem lies below the first divider and outside of the scope of Bookmarks.

Right clicking the menus and saying "Edit Menus" allows me to edit the "Applications" and "System" menus (gah! not the "Places").  gconf, .gnome* directories and *.menu files have found to be un-useful to me (though it is possible that the answer may lie with the configuration of these files)

Partitions that are automatically mounted at boot time do not show up in the Places menu (I currently have such a partition at /dos).  But I don't want the partition to be touched at all at boot time, I don't want it mount at all unless I explicitly tell it to through an explicit mount command.  Somewhere in boot time, the computer is looking at all the partitions that are not being mounted and adds them to the list of partitions to be displayed in the "Places" menu.

I've read a bit of the GNOME configuration link, section 2, but haven't really absorbed too much.  I can give it another go, it's just, I'm having trouble finding the relevant file to begin with, and I find that the greater issue.

Any suggestions?

---

### Post by sdennie on 2008-07-05
I believe that if you mount things via /etc/fstab with the noauto mount option and mount them in /mnt, it will do what you want.  It won't mount at boot time and it won't show up as a gvfs managed partition (only things in /media and /home/* are "controlled" by gnome/nautilus/gvfs).

---

### Post by vanadium on 2008-07-05
> I believe that if you mount things via /etc/fstab with the noauto mount option and mount them in /mnt, it will do what you want.
Only the second part is correct. "noauto" would cause your partition not to be mounted at startup. Thus, just move the mout point from /media to /mnt and update your /etc/fstab to prevent a volume from appearing in "Places".

The appearance of the "special" folders such as Music is controlled by a configuration file. I found a blog on this here: [http://www.movingtofreedom.org/2007/10/23/new-dirs-in-gutsy-documents-music-pictures-video/](http://www.movingtofreedom.org/2007/10/23/new-dirs-in-gutsy-documents-music-pictures-video/)

[edit] I guess you can just remvove these places from the "places" menu by removing them in the Places side panel (right-click - Delete)

---

