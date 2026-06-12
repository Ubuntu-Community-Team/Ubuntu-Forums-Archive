---
title: "&quot;fdisk -l&quot; Incorrect?"
date: 2009-02-19
forum: General Help
---

### Post by nrogers64 on 2009-02-19
Hi there,

I have attempted to format a 300 GB NTFS drive with a single primary partition to ext2. These are the steps I took:
--------------------------------------------------
1.) Boot the computer using a live CD of Ubuntu ([http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download))

2.) Ubuntu will have automatically mounted the USB hard drive (as shown by the icon on the desktop), so you'll need to unmount it or else you won't be able to build the file system. Do this by right-clicking the USB hard drive's icon on the desktop and choosing "Unmount Volume"

3.) Open the terminal by going to the "Applications" menu, then "Accessories", and then "Terminal"

4.) Type "sudo fdisk -l" to see a list of the partition tables. [This is so that you can see which disk the USB hard drive is registered under. An example of this is "/dev/sdb"]

5.) Type "sudo mkfs -t ext2 [device][partition number]" (example: "sudo mkfs -t ext2 /dev/sdb1"). [This builds an ext2 file system on the first partition of the USB hard drive]
--------------------------------------------------
After doing that, I typed "sudo fdisk -l" again to confirm that it worked and it's still reporting that the drive's partition is NTFS. I also tried opening the drive via the "Computer" window, but it reported an NTFS error. I then rebooted and it worked in the "Computer" window, but "sudo fdisk -l" still reported an NTFS partition. However, right-clicking on the icon and looking at its properties shows ext2. Which is right?

Thanks!

---

### Post by unutbu on 2009-02-19
Type
```
sudo sfdisk -c /dev/sdb 1 83
```

The filesystem has a type and the partition which contains the filesystem also has a type. The mkfs -t ext2 command creates a filesystem of type ext2. But it does not change the partition type. The sfdisk command above will change the partition type of sdb1 to 83 (Linux).

In the future, if you use a partition editor like GParted (System>Admin>Partition Editor), and if you delete the NTFS partition and simply create a new Linux partition in its place, you will not need the sfdisk command.

---

### Post by nrogers64 on 2009-02-19
Thank you!

---

### Post by dcstar on 2009-02-19
> **unutbu said:**
> 
..........
In the future, if you use a partition editor like GParted (System>Admin>Partition Editor), and if you delete the NTFS partition and simply create a new Linux partition in its place, you will not need the sfdisk command.

OT - You do wonder when people will stop "recommending" that users use terminal commands (that they don't understand) to achieve something that an existing GUI tool can do.

There still seems to be some perverse "snobbishness" that compels some people to always offer a command line solution when it is far more appropriate for the average Linux user to be given the GUI tool that they will be more familiar (and comfortable) to use.

It may be convenient (and tempting) for us to offer "just type this in a terminal" when we are personally familiar with the particular commands/tools, but is it the best thing for most users now if there is a GUI alternative?

---

### Post by mb_webguy on 2009-02-19
I agree completely, and try to do so whenever possible, but...  It really is easier to say "type this" than to say "click here, then click here, then click here, then..." to do the same thing.

---

### Post by gigo6000 on 2009-03-11
> **mb_webguy said:**
> I agree completely, and try to do so whenever possible, but...  It really is easier to say "type this" than to say "click here, then click here, then click here, then..." to do the same thing.


I agree too

---

### Post by heindsight on 2009-03-11
> **dcstar said:**
> OT - You do wonder when people will stop "recommending" that users use terminal commands (that they don't understand) to achieve something that an existing GUI tool can do.

There still seems to be some perverse "snobbishness" that compels some people to always offer a command line solution when it is far more appropriate for the average Linux user to be given the GUI tool that they will be more familiar (and comfortable) to use.

It may be convenient (and tempting) for us to offer "just type this in a terminal" when we are personally familiar with the particular commands/tools, but is it the best thing for most users now if there is a GUI alternative?

While I agree that having inexperienced users blindly entering commands in a terminal without understanding what they're doing is problematic, I still prefer to give terminal commands - though I usually also try to explain what the commands do and/or advise people to read the manuals.

I have 2 good reasons for preferring terminal commands over GUI instructions. 

Firstly, with the various different GUI environments (GNOME, KDE, XFCE) it's extremely difficult to give users instructions that will work across the board (eg, since I know GNOME but not KDE or XFCE I'd only ever be able to help GNOME users), this problem is further complicated by things such as language (eg. different localisations use different labels for menus, tabs, etc) and the level to which users can customise their own desktops (items can be removed from menus, menu labels can be changed, shortcut keys can be changed etc). Also, the GUI is less stable from one release to the next (eg in the past some options have been moved from one dialog to another or new dialogs were introduced). Thus I may run into trouble helping anyone other than english speaking users running GNOME in 8.04.

Secondly, to me the GUI is simply a toy, used for playing games, browsing the web, watching movies etc. Any real work I do from the command line interface. This means that 90% of the time I don't even know how to accomplish various tasks using a GUI. For example I have no idea how to find a bunch of files and perform some operation on them using a GUI. If someone wants to reformat a partition from NTFS to ext3, the best GUI advice I could give would be to say "I believe you can use gparted for that" whereas I could explain to them exactly what steps to take to complete the task in a terminal (including what each command does and why).

EDIT:
I might add that in the hands on an inexperienced user, a GUI can be just as dangerous as a terminal. Many routine admin tasks require root access. In the GUI, many such tasks would require a user to run Nautilus (or whatever KDE and XFCE equivalents are) as root which imho is much more dangerous than running a few terminal commands using sudo.

---

