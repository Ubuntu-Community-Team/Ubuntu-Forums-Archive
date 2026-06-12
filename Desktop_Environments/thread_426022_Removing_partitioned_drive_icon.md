---
title: "Removing partitioned drive icon"
date: 2007-04-28
forum: Desktop Environments
---

### Post by NotoriousTF on 2007-04-28
Hello all!

I've just a simple question about desktop icons, relating to the volumes that are mounted. Since my laptop is running a dual-boot, on my desktop the partitioned drive is always visible, along with any other devices that are mounted. I'm just wondering if there is a way which I could leave icons such as usb drives and cd's visible, but have the partitioned icon removed? I know using nautilus all the icons for volumes can be made disappear, so have I overlooked something in there?

---

### Post by louistan3 on 2007-04-28
uhmm if u dont want them mounted at bootup...

could try commenting them out of your /etc/fstab

or if you still want them mounted...

you could mount them in another folder at bootup..

do this by creating lets say /mnt folder in root directory..

then edit your fstab, change the mount points of the partitions you want to /mnt/<mount-folder>

and uhmm restart...

by doing the second way.. you could still access your other partitions..

hope this is what your looking for.. 

:)

---

### Post by NotoriousTF on 2007-04-30
Ok thanks louis, I'll give that a try tonight and let you know if it worked!

---

### Post by Jadd on 2007-05-01
No, that will stop Ubuntu from accessing those partitions all togethor, I think what Notorious meant was removing the partition *icons* from his desktop. I also can't find a way to do this.

---

### Post by oomingmak on 2007-05-01
> **NotoriousTF said:**
> I've just a simple question about desktop icons, relating to the volumes that are mounted. Since my laptop is running a dual-boot, on my desktop the partitioned drive is always visible, along with any other devices that are mounted. I'm just wondering if there is a way which I could leave icons such as usb drives and cd's visible, but have the partitioned icon removed? I know using nautilus all the icons for volumes can be made disappear, so have I overlooked something in there?

No, you are not overlooking anything (as far as I know). I'm a noob, but I've looked into this situation and there was no work-around other than to create a program to do it.

A guy on this forum has made this:

[http://ubuntuforums.org/showthread.php?t=421266](http://ubuntuforums.org/showthread.php?t=421266)

Its aims to do what you describe (although I installed it and it didn't work for me). You may have more luck with it than I did. Hopefully later versions of chakkaradeep's utility will work for me.

Gnome really should have had a gconf-option to show/hide removable drives and a separate option show/hide fixed drives (instead of the coarse and clunky all or nothing approach that they have at the moment). I would have thought that it's pretty obvious these two categories of drive will generally be treated quite differently by users.

I'd also like to have unused icons (i.e. unmounted partitions) removed from the Places bar.  I do not want Linux going anywhere near my Windows partitions (whether they be unmounted or not). 

There really is no point having icons in the places bar for partitions that you can't even use (because they're not mounted) and you can always use 'Computer' if you decide that you want to access them at a later date, so cluttering the Places bar with unmounted partitions is something I'd like to get rid of.

---

### Post by NotoriousTF on 2007-05-01
Yeah thanks Jadd, I'm only looking to remove the icons not preventing the OS from accessing the partitions. I was sort of confused there for a bit!!
Thanks for the link oomingmak, I hadn't found anything on the forums about it but I was pretty sure there had to be something out there. I'll definitely give that program a try and see if I can get it to work. Although I've been using Ubuntu for a while now, I'm still new to everything that goes on 'behind the scenes' too!

---

### Post by louistan3 on 2007-05-01
remounting the partitions to another mount point does not stop ubuntu from accessing the partitions...

its just that ubuntu sets the automatic icons if there is anything mounted on the /media directory..

so moving it to another mount point in the filesystem would still allow access but no more icons..

unless you really need them mounted to /media/<mount>

but i really think this should do what you want.. 

if not.. then i hope you find a solution.. :)

---

