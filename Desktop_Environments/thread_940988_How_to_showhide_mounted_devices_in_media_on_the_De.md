---
title: "How to show/hide mounted devices in /media on the Desktop"
date: 2008-10-07
forum: Desktop Environments
---

### Post by fermulator on 2008-10-07
Removable storage devices that get attached to the system are automatically mounted in /media, and an icon placed on the desktop.  This is excellent behaviour.

However, if a user has several other partitions (perhaps Windows NTFS partitions), they're also mounted in /media, but we might not want to see ALL of these partitions on the desktop (clutter).

**_GOAL_**
 - Partitions to be shown in "Computer" (computer:///)
 - Selectively choose which of these partitions may or may not appear as icons on the desktop

How can we accomplish this?  I see an [older thread]("http://ubuntuforums.org/showthread.php?t=580599") talking about simply mounting the drives somewhere else (i.e. /mnt), but then the partitions wouldn't appear in "Computer".  I also found a [kubuntu article]("https://wiki.kubuntu.org/MediaOnDesktop") describing a similar functionality/goal ...

Thoughts?

---

### Post by Steve1961 on 2008-10-07
I'm not sure that you can selectively display mounted volumes on the desktop.  However, you can use the options in Applications/System Tools/Configuration Editor then apps/nautilus/desktop to turn showing mounted volumes on the desktop on or off.  I turn the option off and access all volumes from the nautilus side-bar instead, which keeps things neat.

The configuration editor isn't shown in the menu in the default setup, but just right-click the panel menu and select edit, and tick the box in the menu editor to show it on the menu.

---

### Post by lian1238 on 2008-10-07
You can turn off showing mounted volumes like **Steve1961** suggested. Then manually create a launcher (right-click on desktop->create launcher..) to that location in /media. In won't be exactly the same, but it works.

---

### Post by ajgreeny on 2008-10-07
I also read that you can change the mount points of devices if you wish to mnt rather than /media and those in mnt will not show on the desktop but will still be mounted if you want to access them.  I've never tried this so can not tell you if it is correct, but it should be worth trying.

Personally, I keep all my other devices, eg windows and other linux distro partitions unmounted and therefore not showing on the desktop.  I then quickly mount them if needed with the panel applet "Disk Mounter".  Simple but effective.  I hardly ever need to find anything on my windows partition these days.  In fact I really have hardly any use for windows any more, but I paid for it so I keep it at the moment.

---

### Post by fermulator on 2008-10-16
Hum, this is rather unfortunate then based on some of your responses.  Seems strange that there's no control over such a thing.

The *ideal* case is that we see the filesystems in "Computer", but not on the desktop.  At the same time however, if we insert removable media (USB key, camera, etc.), the device should be mounted automatically into /media and show in "Computer" AND the "Desktop".

i.e. - "Computer" should be a nice overall view of all of your devices (just like Windows would show I suppose).  Your desktop is customizable.

 .... hummmm ....

---

### Post by fermulator on 2008-10-24
bump! ;-0 *crosses fingers*

---

### Post by lian1238 on 2008-10-25
What I did was mount the unwanted drives elsewhere, i.e. I now have nothing mounted at /media. I did this because I still want to see the mounted USB drives.

---

### Post by fermulator on 2008-10-28
> **lian1238 said:**
> What I did was mount the unwanted drives elsewhere, i.e. I now have nothing mounted at /media. I did this because I still want to see the mounted USB drives.

That's what I have now.  All of my static partitions (ntfs-3g, ext3, cifs, etc.) are all mounted in **/mnt**.

However, given this list of mounted devices in /mnt, how can we show them in the "computer:///" view (Places --> Computer)?

---

### Post by fermulator on 2009-05-16
> **fermulator said:**
> given this list of mounted devices in /mnt, how can we show them in the "computer:///" view (Places --> Computer)?

?

---

### Post by cariboo on 2009-05-16
I usually mount partitiosn using /etc/fstab, that way they don't show on the desktop, but are available in either Nautilus or Computer. I'm running Karmic, and to keep email in sync between it and Jaunty I mount the partiton that Jaunty is on and use a symlink to the .mozilla-thunderbird directory. I use the following command in /etc/fstab to automount he partition:

```
#Jaunty home for email link
UUID=7c109a7f-b7fd-402d-aec5-0ee7dd30d37a /home/internal	ext4	relatime  0	2
```

---

### Post by fermulator on 2009-05-16
Things mounted in /mnt (or otherwise) are indeed available in Nautilus, simply by browsing to the "Filesystem" (/), but they're NOT visible in "Computer".

I'm wondering how to show these partitions in the "Computer" (computer:///).

---

### Post by lian1238 on 2009-05-16
> **fermulator said:**
> 
However, given this list of mounted devices in /mnt, how can we show them in the "computer:///" view (Places --> Computer)?
I put my mounted drives in Places. In nautilus, press F9 and bring the shortcuts. Drag to the side pane.

---

### Post by fermulator on 2009-05-27
> **lian1238 said:**
> I put my mounted drives in Places. In nautilus, press F9 and bring the shortcuts. Drag to the side pane.

True, "Places" or "Bookmarks" are useful.  But if someone wants to see all PHYSICAL drives in the "Computer" view (which I think makes a lot of sense, regardless of your bookmarks), the question still remains ... how to do it?

---

### Post by jfjunior on 2009-06-12
> **fermulator said:**
> Removable storage devices that get attached to the system are automatically mounted in /media, and an icon placed on the desktop.  This is excellent behaviour.

However, if a user has several other partitions (perhaps Windows NTFS partitions), they're also mounted in /media, but we might not want to see ALL of these partitions on the desktop (clutter).

**_GOAL_**
 - Partitions to be shown in "Computer" (computer:///)
 - Selectively choose which of these partitions may or may not appear as icons on the desktop

How can we accomplish this?  I see an [older thread]("http://ubuntuforums.org/showthread.php?t=580599") talking about simply mounting the drives somewhere else (i.e. /mnt), but then the partitions wouldn't appear in "Computer".  I also found a [kubuntu article]("https://wiki.kubuntu.org/MediaOnDesktop") describing a similar functionality/goal ...

Thoughts?
There is an easy way to accomplish what you are looking for. Here it is: [http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/](http://www.howtogeek.com/howto/ubuntu/hide-removable-drive-icons-from-your-ubuntu-desktop/)

---

### Post by PureLoneWolf on 2009-06-12
That isn't what the OP is asking for.

Think back to your Windows days (presuming you had them).

Open up "My Computer" and you see all logical drives (ie anything with a drive letter assigned).  You could then start browsing at that point through any defined partition.

Obviously linux doesn't handle logical drives in this manner and mounts everything under folders.  The OP would like to see each of his hard disks listed when you open Computer (Places/Computer)

Currently it shows any CD/DVD Drives and floppy drives plus filesystem.  He would like anything that is mounted under filesystem somewhere to be placed there too.

THat all said, I have never seen this done in Linux...so can't help, but hopefully someone else has and my take on the OPs request might help

Cheers

---

### Post by lian1238 on 2009-06-17
If you want physical drives to show up in My Computer, you need to mount them in /media. If you currently have them mounted somewhere else, move them to /media and make a symbolic link. "ln -sf <target> <link_name>".

And of course, if you want them to show on the Desktop as well, you need to run gconf-editor, and check: /apps/nautilus/desktop/volumns_visible

---

### Post by fermulator on 2009-06-19
Thanks for all of the tips.

The concept of mounting devices (either using fstab or symlinks) in /media still does not solve the problem.

If you mount into /media, the devices show up in "Computer" (yay!), but they still show up on the Desktop.  OK, you can go into gconf editor and uncheck "show volumes" ... but then your removable media devices don't show up on the desktop!  :-(

---

### Post by lian1238 on 2009-06-20
> **fermulator said:**
> Thanks for all of the tips.

The concept of mounting devices (either using fstab or symlinks) in /media still does not solve the problem.

If you mount into /media, the devices show up in "Computer" (yay!), but they still show up on the Desktop.  OK, you can go into gconf editor and uncheck "show volumes" ... but then your removable media devices don't show up on the desktop!  :-(
I guess it's an all-or-nothing option. Personally, I like to hide all physical drives as I don't need to go to My Computer to access my Pictures, Music, or Downloads.

---

### Post by fermulator on 2009-06-20
Well, consider this scenario:

A user has .. 12 paritions. (they have lots of hard drives, and have some crazy desire to segregate stuff).  They want something similar to what I have.

To list ALL of those physical partitions as bookmarks isn't really feasible because once you surpass 6(?) bookmarks, it collapses into a sub menu in gnome.

Anyways, I think I'm realizing that it "isn't possible" with the current gnome.  Where is the best place to go at this point to request for an implementation?

---

### Post by lian1238 on 2009-06-21
The bookmarks get collapsed in Places, yes. But, not in nautilus. If you open the sidebar in nautilus (F9), you'll see a list of all the bookmarks.

---

### Post by TiredBird on 2009-09-14
My system, (Ubuntu Jaunty 9.04 with Gnome desktop as installed), doesn't distinguish between media that is mounted on /media or media that is mounted elsewhere. Some of it appears as icons on the desktop and some of it doesn't. I can shut all of it off from the gconf-editor but I can't seem to get just part of it to show.

Examples: (with the Nautilus 'show on desktop' checked)

1) Two NFS mounts (on /mnt) don't appear - ok;

2) The mounts of seven local hard-drive partitions do not appear, (all mounted at places other than /media) - ok;

3) A bind mount of the root partition, mounted on itself but not on /media does not appear - ok;

4) 21 bind mounts of various portions of previously mounted partitions which are mounted at various points in my /home/xxxxx directory, (none on /media), DO show up on the desktop - NOT OK!;

5) A USB flash-drive (which gets automatically mounted on /media) does show up - OK;

6) 4 encrypted file system containers from /home/xxxx are decrypted by Truecrypt and mounted at various points in the /home/xxxx directory - all show on the desktop - OK;

All of the items that appear on the desktop also appear in //computer. I have to turn off the nautilus desktop icons to get rid of the clutter on my desktop caused by the 21 bind mounts described in #4 above, but unfortunately, that also leaves me with no readily visible indication of the USB stick that is mounted on /media or of the decrypted volumes that are mounted on my home directory.

I can't seem to make any sense out of it. If I just knew why some items have icons and others do not, I could probably restructure accordingly.

Any additional help would be greatly appreciated.

---

### Post by TiredBird on 2009-09-15
My problem has been solved, thanks to [this post]("http://ubuntuforums.org/showpost.php?p=7328167&postcount=4"). 

Having learned that mounts in /media AND in /home/xxxx BOTH cause icons to be placed on the desktop, I have been able to change the 21 bind mounts I had in the home directory to soft links and fixed my problem.

I have turned the nautilus desktop icons back on, (gconf-edit) and now the only things that show up on the desktop are from hot-plugged media (which is automatically mounted in /media) and the Truecrypt decrypted containers that are mounted in /home/xxxx. That's exactly what I want and with the links I have less mounts, smaller fstab, less code and faster startup and shutdown.

Thanks to all!

---

