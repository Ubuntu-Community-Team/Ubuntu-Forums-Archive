---
title: "Removing drive shortcuts from the Files Side Panel 15.10"
date: 2016-06-12
forum: Desktop Environments
---

### Post by akash16 on 2016-06-12
Hi,

How do we remove the drive shortcuts from the Files side panel?  I tried right clicking the shortcut, but doesn't show an option to remove/hide it. I am looking for a way to remove it permanently.

Thanks !!!

---

### Post by ajgreeny on 2016-06-12
What drives are showing at the moment; I assume they are all drive partitions that are mounted in fstab or on usb mounted disks and automounted in /media?  The OS partitions mounted by fstab will normally show as volumes in the left hand pane of file-managers as far as I'm aware, and I'm not sure you can change that behaviour, though it may be possible if you can edit the code that does that job, but that is way beyond my abilities.  Any USB disks that show can be made to mount in /mnt if you add them to, and mount them using fstab, but that means there will be a hiccup in the boot process if the usb disk is not always attached.

There is a similar discussion, perhaps for a different reason at [http://ubuntuforums.org/showthread.php?t=2326313](http://ubuntuforums.org/showthread.php?t=2326313) which you may wish to read through to see if it helps you.

---

### Post by vasa1 on 2016-06-12
Or maybe this: [http://ubuntuforums.org/showthread.php?t=2322465&p=13502842#post13502842](http://ubuntuforums.org/showthread.php?t=2322465&p=13502842#post13502842) ?

---

### Post by CantankRus on 2016-06-12
You can use Disks (gnome-disk-utility). Just search disks in the dash.
In Disks click on a partition then hit the 2 little cog wheels.
Select "Edit Mount Options..."
[ATTACH=CONFIG]269537[/ATTACH]

In the popup window, disable "Automatic Mount Options" which then allows you to select whether to "Show in user interface".
[ATTACH=CONFIG]269538[/ATTACH]
The change is visible instantly in Files.

You will see any mount changes reflected in your **/etc/fstab** file.

---

### Post by akash16 on 2016-06-12
@ajgreeny - Its the shortcut to drive partition that I am trying to remove 

I will try out the suggested options and update the thread. - Thanks!

---

