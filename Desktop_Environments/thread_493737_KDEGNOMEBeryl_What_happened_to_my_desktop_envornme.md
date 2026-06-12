---
title: "KDE/GNOME/Beryl? What happened to my desktop envornment?"
date: 2007-07-06
forum: Desktop Environments
---

### Post by Lolicon on 2007-07-06
I have a few partitions that don't automount on my computer. I decided to just use Nautilus to mount them manually everytime. Only problem is when I launched it, the icons and my desktop changed and now Beryl+KDE on it looks exactly like Gnome. I hate it. How can I revert it, and is there some sort of other program I can use to mount my partitons manually or maybe write a script? Thanks...
[img]http://img207.imageshack.us/img207/165/snapshot1gx9.jpg[/img]

---

### Post by JanvL on 2007-07-06
Hi,

At first, what kind of partitions?
Are they on a harddisk in the machine?
Do you want to mount them every time you start the machine?
Are they NFS partition?
Or SMB-shares?

For HD's inside the machine edit fstab.
How to do that is described in detail under "man fstab" use google if you need more info.

If you want to mount them by hand or over a script, this is possible for
"normal", NFS, SMB.

You must make a mountpoint in the existing filesystem however, this is easy
just make a directory where you want to "plugg-in" the partition and leave it
empty, after mounting the partition is "in there", after unmounting it is empty again.

Lots of success.

Jan

---

### Post by Lolicon on 2007-07-06
Well, I used an ext2 drive on my Windows machine, so they show up as ext2, but they're actually ext3. They are partitions of one hard drive.
My fstab is over here...
[http://ubuntuforums.org/showthread.php?t=493741](http://ubuntuforums.org/showthread.php?t=493741)

Any idea what happened to my desktop enviornment?

---

### Post by Lolicon on 2007-07-06
Found out that Nautilus is a shell too. SIGKILLED it for anyone who might have the same problem.

---

