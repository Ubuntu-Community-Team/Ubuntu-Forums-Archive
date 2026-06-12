---
title: "How to edit PLACES menu (not bookmarks!)"
date: 2008-12-03
forum: General Help
---

### Post by solwic on 2008-12-03
I'm trying to edit my places menu.  I know about the bookmark thing, that's not what I'm looking for.  I've been scouring the net for hours trying to find this, with no luck, so I thought I'd post here.

I want to edit the Places menu.  Say, get rid of the "CD/DVD Creator", "Network", "Connect to server..." links.  I never use them, they're annoying, and I hate them.  Yet there's no way to remove them.

At least, no way I can find.  Like I said, it's not a bookmark thing.  

Any ideas?  I've been all over the forums and Google...no luck.  Any help here would be awesome.  

Thanks!

P.S.  Ubuntu 8.04, btw.  If it matters.

---

### Post by solwic on 2008-12-03
*bump*

Anybody?

---

### Post by solwic on 2008-12-04
*bump*

Anybody at all?  Or can this not be done?

---

### Post by solwic on 2008-12-04
I guess I'm giving up on this for now.  Until I find evidence to the contrary, I'm assuming that this is something that isn't possible.  

Thanks anyway to all those who read the post.  :)

---

### Post by ddixonr on 2008-12-04
Also needed here... Specifically I'd like remove the Bookmarks submenu and just list them all down the screen.

---

### Post by DJGQ on 2009-01-12
Old topic, but I was looking for the answer.

---

### Post by Jameshardy88 on 2009-01-12
im also interested as i would like to add the filesystem to the menu

---

### Post by daprofessor on 2009-01-12
Here is the answer

[http://thetechturf.com/?p=462]("http://thetechturf.com/?p=462")

---

### Post by ogara0c9 on 2009-02-19
This does not solve the threads original problem.  We are looking for a way to add/remove things like the cdrom drive or in my case the 90GB media drive representing my Windows partition.  We are not interested in the bookmarks.  Please read the thread title and posts.

---

### Post by mb_webguy on 2009-02-19
[This]("http://ubuntuforums.org/showpost.php?p=6677262&postcount=2") should help at least with hiding your Windows partition.  It should probably also allow you to hide the disc drive (though I wouldn't suggest it unless you don't actually have a disc drive, since it would prevent it from ever showing up, even when you have a disc loaded).

---

### Post by DrHow on 2009-05-12
I was going to start this this thread before I discovered that it already exists.  I am astounded by the fact that there is no good answer at all (aside from hiding certain partitions).  

As an example, I find that I frequently want to go to /usr, and doing so is cumbersome.  I can create a Launcher for /usr, but I cannot drag and drop it on the Places menu.  

If you right click on unused space in the Places menu, there is an option to "Edit Menus".  However, the menu editing software does not allow one to edit the Places menu.  I tried to create a "Places2" submenu in the Applications menu.  The New Item dialogue allows specification of locations as opposed to applications, but I was unable to make it work.

What gives?  This should not be so hard.

---

### Post by mikewhatever on 2009-05-12
You can easily add /usr to Nautilus' bookmarks.

---

### Post by DrHow on 2009-05-13
> **mikewhatever said:**
> You can easily add /usr to Nautilus' bookmarks.

Yes; but, if that is the solution, then why do I need the Places menu at all?  It would then make more sense to always just launch the file browser first, rather than to evoke the Places menu.

My own intermediate solution (until the Ubuntu developers have provided support for editing the Places menu) is to put a launcher for /usr (and a couple of other places I frequently visit) on the panel.

I tried the procedure to hide certain partitions, but I could not make it work.  The partitions I wanted to hide were a small system-description partition and a recovery partition, neither of ongoing interest.  I actually want Ubuntu to be able to mount the partition in which Vista is installed.

---

### Post by mikewhatever on 2009-05-14
I don't understand. If you add /usr to bookmarks in Nautilus, the entry will show in Places as well as in the left panel. I've tested it just now. You can then open /usr location either by selecting Places->usr, or by opening the file browser and navigating to /usr. In fact, you can create bookmarks to any location, and they'll show under places.

As for removing entries, the solution suggested worked very well. I just hid sda1, sda2 and sda3, all Windows related partitions.

---

### Post by CatKiller on 2009-05-14
To people who actually want to remove the default entries on the Places menu, they are .desktop files in /usr/share/applications, the same as the other menu entries. The Places -> Home Folder launcher is /usr/share/applications/nautilus-home.desktop, for example. You can change these the same as any other .desktop file, including by putting Hidden=True in there. This will change it for all users, but since most of the people who request this appear to be on single-user systems, it will do. Otherwise you can create .menu files that will exclude those .desktop files for just one user.

To DrHow, adding a bookmark will automatically add an entry to the Places menu, as mikewhatever said. If you want your Vista partition to be mounted, you can add an entry for it in /etc/fstab so that that partition gets mounted and you don't have to see the others on your Desktop.

---

### Post by DrHow on 2009-05-14
> **CatKiller said:**
> 
To DrHow, adding a bookmark will automatically add an entry to the Places menu, as mikewhatever said. 

He did not say that adding the bookmark in Nautilus would have the Places side effect I was seeking.  I figured that the bookmark would only help me if I invoked the file browser, so I did not even try his suggestion.  Now I will.

> If you want your Vista partition to be mounted, you can add an entry for it in /etc/fstab so that that partition gets mounted and you don't have to see the others on your Desktop.

I don't need for it to be mounted by default; but it would be nice if that icon did not have to appear on the desktop when it is mounted.  If the fstab approach has this effect, then I will mount it by default.  

I don't understand about "others", as none appear on the desktop until I actually access them.  There are other partitions besides the Vista one which are not mounted by default and which I do wish to access at times.  However, the two from the computer manufacturer certainly do not need to be seen ever in Ubuntu.


The advice about the .desktop files is the sort of answer I would have been expecting as the answer to the question of this thread.  There had to be a file somewhere describing the Places menu.  I just had no idea where to look, since my search on files with "places" in the name was not productive.

---

### Post by DrHow on 2009-05-14
> **mikewhatever said:**
> I don't understand. If you add /usr to bookmarks in Nautilus, the entry will show in Places as well as in the left panel. I've tested it just now. You can then open /usr location either by selecting Places->usr, or by opening the file browser and navigating to /usr. In fact, you can create bookmarks to any location, and they'll show under places.

I did not understand about the side effect, so the above explanation would have been more helpful the first time around.

> As for removing entries, the solution suggested worked very well. I just hid sda1, sda2 and sda3, all Windows related partitions.

I must have blundered when I tried to implement it.  Alas, when I just tried again to visit the page where it is described, I discovered that the reference is no longer valid because the blogger is changing from Wordpress to Joomla.  Is there an alternative route to that advice?  I just found some advice apparently addressing the same issue: [http://ubuntuforums.org/showthread.php?t=668748](http://ubuntuforums.org/showthread.php?t=668748)
Maybe that will work for me.

---

### Post by mikewhatever on 2009-05-14
> **DrHow said:**
> 
I must have blundered when I tried to implement it.  Alas, when I just tried again to visit the page where it is described, I discovered that the reference is no longer valid because the blogger is changing from Wordpress to Joomla.  Is there an alternative route to that advice?  I just found some advice apparently addressing the same issue: [http://ubuntuforums.org/showthread.php?t=668748](http://ubuntuforums.org/showthread.php?t=668748)
Maybe that will work for me.

I used [this link]("http://ubuntuforums.org/showpost.php?p=6677262&postcount=2").
The partitions disappeared from places immediately, without rebooting.

---

### Post by HavocXphere on 2009-05-14
Firefox->File->Save As.

Browse to the folder you want to add and select it. Bottom left, select Add.

Or am I misunderstanding the Q?

---

### Post by CatKiller on 2009-05-14
> **DrHow said:**
> He did not say that adding the bookmark in Nautilus would have the Places side effect I was seeking.  I figured that the bookmark would only help me if I invoked the file browser, so I did not even try his suggestion.  Now I will.

Of course. I was just reiterating that it was probably the solution that you were after.

> 
I don't need for it to be mounted by default; but it would be nice if that icon did not have to appear on the desktop when it is mounted.  If the fstab approach has this effect, then I will mount it by default.  

I don't understand about "others", as none appear on the desktop until I actually access them.  There are other partitions besides the Vista one which are not mounted by default and which I do wish to access at times.  However, the two from the computer manufacturer certainly do not need to be seen ever in Ubuntu.


Fair enough. There is a setting for whether icons get put on the desktop when a partition is mounted in /media (which is the default location for removable drives). In gconf-editor, it's the /apps/nautilus/desktop/volumes_visible setting. Or you can put an entry in fstab that mounts the partition somewhere other than /media. /mnt is a commonly-used location for this purpose. If you don't want the partition to be automatically mounted, it doesn't have to be. Once you've got the entry in /etc/fstab, you can put **noauto** as an option for that line to stop that partition being mounted at boot time. You can then manually mount that partition with **sudo mount <device name>**.

> 
The advice about the .desktop files is the sort of answer I would have been expecting as the answer to the question of this thread.  There had to be a file somewhere describing the Places menu.  I just had no idea where to look, since my search on files with "places" in the name was not productive.

Yeah. The whole .desktop method of doing things is really flexible. Which means that it can be quite hard to find specifics about a particular implementation. Once you've got a starting point it's quite straightforward to find out how to use it, but it's getting the starting point that's a challenge.

Good luck with your customisations.

---

### Post by DrHow on 2009-05-20
> **mikewhatever said:**
> I used [this link]("http://ubuntuforums.org/showpost.php?p=6677262&postcount=2").

Ahh!  Those were the instructions I tried to follow the first time; and I had indeed blundered - having duped the <deviceinfo version="0.2"> line for my second partition to hide.  I fixed that.

> 
The partitions disappeared from places immediately, without rebooting.

I did not get that effect.  I had to reboot before the two partitions I hid disappeared.

But it does work, and I am happy to not see the useless partitions anymore.  Thanks for the pointer.

One interesting thing about the bookmarks side effect in Places is that, once there are enough of them, they go into a submenu of the Places menu.  That's OK by me.

---

### Post by DrHow on 2009-05-20
> **CatKiller said:**
> To people who actually want to remove the default entries on the Places menu, they are .desktop files in /usr/share/applications, the same as the other menu entries. The Places -> Home Folder launcher is /usr/share/applications/nautilus-home.desktop, for example. You can change these the same as any other .desktop file, including by putting Hidden=True in there. This will change it for all users, but since most of the people who request this appear to be on single-user systems, it will do. Otherwise you can create .menu files that will exclude those .desktop files for just one user.

To DrHow, adding a bookmark will automatically add an entry to the Places menu, as mikewhatever said. If you want your Vista partition to be mounted, you can add an entry for it in /etc/fstab so that that partition gets mounted and you don't have to see the others on your Desktop.

When I browsed /etc/ with Nautilus, I could not figure out what Catkiller was talking about.  I even have Nautilus configured to show hidden files, but there is still much that it was not showing me.  (It did not show the .desktop extensions and it did not even offer to open one with an editor.)  When I looked at /etc/ using emacs dired, things became much more clear.  However, editing the .desktop files remains a bit intimidating, since I have not found the instructions for that.  I did find a tutorial on using fstab: [http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by CatKiller on 2009-05-20
> **DrHow said:**
>  However, editing the .desktop files remains a bit intimidating, since I have not found the instructions for that.

Well, the specification is [here]("http://standards.freedesktop.org/desktop-entry-spec/latest/").

When I've been changing them, though, I just look at ones that do what I want, and change others accordingly. That's how I've created launchers for things that don't come with them - like Unreal Tournament - for all users. It works for panel applets, AWN launchers and, in this case, the Places menu.

---

### Post by lasjen on 2010-08-04
I don't know if this will help you, but I was looking for a file to edit these links.
And I found this under ~/.gtk-bookmarks

---

### Post by goronaga on 2010-08-08
Maybe you should try to config user-dirs.dirs file? Try: gedit .config/user-dirs.dirs

---

### Post by bouncingwilf on 2010-08-08
Just to add a further confusion to the scene, I have also been looking high and low as to how to alter the action of the places menu. I my case ( as reported but unanswered [http://ubuntuforums.org/showthread.php?t=1543445&highlight=asunder](http://ubuntuforums.org/showthread.php?t=1543445&highlight=asunder)) trying to get asunder to read a second USB CD drive resulted in the places menu becoming corrupt and selecting most of the entries results in the menu then launches asunder.

I have checked the actions of nautilus - OK
I have confirmed that gtk-bookmarks contains the correct entries so well the H**l do I look to find the actual script that defines the actions taken when you click on the sub-entries of the places menu please?

bouncingwilf

---

### Post by Flos Headford on 2010-09-17
I have read through this list carefully. I have, in my Places menu, an entry called Removable Devices, under which appear partitions I have mounted through Nautilus in the past. The problem is that (for reasons which would probably only make sense to the person who decided on the whacky placement and naming of the nautilus config files) I now have duplicate entries for the same partitions, and some of these, when clicked, produce an Error dialogue which reads as follows:
Unable to Mount SC57G0B
Unprivileged user can not mount NTFS block devices using the external FUSE
library. Either mount the volume as root, or rebuild NTFS-3G with integrated
FUSE support and make it setuid root. Please see more information at
[http://ntfs-3g.org/support.html#unprivileged](http://ntfs-3g.org/support.html#unprivileged)

[I followed the link given, but the info there is not well written, and it's all beyond me at the moment]
SO, all I wanted to do was remove the unfunctional entries from the Places sub-menu.
Anyone else trying to do something similar ought to be aware that -
1) if a partition is mounted on a /media directory, it is treated as "removable". [Thank you for that, CatKiller - it's the only mention I've found in two years of reading!]
2) nautilus HIDES the ~/.gtk-bookmarks directory (another whacky geek decision, no doubt). You need to use a terminal to even see it.
3) the Places menu has several divisions. Only the entries in the top division are bookmarks. These bookmarks can be edited directly from the nautilus menu bar, under Bookmarks->Edit. I've no idea what the other divisions are called.

I edited my fstab, replacing /media with /mnt (and creating the appropriate directories in /mnt).
On reboot, the annoying "Removable Drives" entry in Places had disappeared. I could then add Bookmarks to my data partitions. This is not completely intuitive; you need to open the desired partition, not mereley select (highlight) it when you click on Bookmarks->Add Bookmark (Bookmarks->Edit Bookmarks does not permit additions). I could locate my desired partitions under File System->/mnt.

Thus, I achieved what (I hope) the Original Poster wanted.
Many thanks to all who contributed to this discussion. I leave it to OP to mark this as solved, if apt.
Phil Headford

---

### Post by khormin on 2011-03-01
Necro (apologies), but huge thanks.  Was having issues with duplicate drive entries in Places thanks to changing into NTFS-3G on fstab.

Followed the guide above (especial thanks to CatKiller), remapped all drives to /mnt instead of /media, worked like a charm.

Now just trying to get my Ubuntu to stop deleting the /mnt folder for a spare ext4 drive I have whenever it logs out of it. '=)

---

### Post by andrei77 on 2012-07-21
[http://ubuntuforums.org/showthread.php?t=1436545](http://ubuntuforums.org/showthread.php?t=1436545)

---

### Post by wildmanne39 on 2012-07-21
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

