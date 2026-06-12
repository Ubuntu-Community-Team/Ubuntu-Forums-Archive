---
title: "Forgot to mount /home partition on install"
date: 2009-03-27
forum: General Help
---

### Post by nicol_bolas on 2009-03-27
How do I mount a /home partition on boot?

Thank-you,
Nicol_Bolas

---

### Post by neilevan814 on 2009-03-27
When you installed the operating system did you create a separate partition that you wanted to use for /home?  Because if you have a partition created, you could follow one of these guides here:

[https://help.ubuntu.com/community/InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive") 

[http://ubuntuforums.org/showthread.php?t=1090095]("http://ubuntuforums.org/showthread.php?t=1090095")

This may help a little.

---

### Post by nicol_bolas on 2009-03-27
> **neilevan814 said:**
> When you installed the operating system did you create a separate partition that you wanted to use for /home?  Because if you have a partition created, you could follow one of these guides here:

[https://help.ubuntu.com/community/InstallingANewHardDrive]("https://help.ubuntu.com/community/InstallingANewHardDrive") 

[http://ubuntuforums.org/showthread.php?t=1090095]("http://ubuntuforums.org/showthread.php?t=1090095")

This may help a little.

Thank you, but that is not what i needed.
I have a partition on my hard drive that I have set up for my home partition; however, I did not set it up as my home partition when I reinstalled Ubuntu.

---

### Post by lemuriaX on 2009-03-27
I´m not an expert on this but you might find the tutorial here useful:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

That´s for creating a separate /home partition if you already installed Ubuntu without a /home partition (i.e., /home is just a folder inside your / partition)

Edit: Obviously you already have a separate partition you want to use as /home -- but the part about how to use the new partition might help, not sure.

---

### Post by ryanhaigh on 2009-03-27
What you need is actually in here:
[https://help.ubuntu.com/community/InstallingANewHardDrive:](https://help.ubuntu.com/community/InstallingANewHardDrive:)
>  /dev/sdb1    /media/mynewdrive   ext3    defaults     0        2

For your situation you would want something like:
>  /dev/sdXX    /home   ext3    defaults     0        2
Where you will need to replace XX with the details for the drive that has your /home partition on it.

---

### Post by mb_webguy on 2009-03-27
If I'm understanding you correctly, then you have a partition already formatted and sitting there waiting to be used as your home directory, but you forgot to mount it during installation, correct?

If that's the case, then mounting it is only slightly more complicated than... well, mounting it.

First, find out what you need to know to mount it.  Use the command "sudo fdisk -l" to list your partitions, and identify the device listed for the partition you want to use as your home directory.  Write this down or copy it somewhere, so you don't forget.  Now use the command "ls /dev/disk/by-uuid -alh" to identify the UUID (the long alphanumeric string) associated with the drive by cross-checking it with the device number.  Copy the UUID somewhere, since we'll be using it later.

Now mount the partition temporarily with the following commands, substituting the approprate device ID for *xxxn*.  Then copy the contents of your current home directory to the newly mounted partition.```
sudo mkdir /mnt/newhome
sudo mount /dev/*xxxn* /mnt/newhome
sudo cp -r /home /mnt/newhome
```
Now we need to edit the fstab file so the partition will be mounted as home on startup.  Use the command "gksu gedit /etc/fstab" to open the file, then add the following line, substituting the appropriate device ID and UUID for your partition.  (Note that the important thing here is the UUID.  The first line is just a comment to make things easier for you if you want to edit fstab later.)```
# /dev/*xxxn*
UUID=*lots_of_letters_and_numbers* /home           ext3    relatime        0       2

```
Now you only have one problem -- you have two different home directories.  You need to delete the one you don't want anymore, but you can't do that while you're using it.  So boot up a LiveCD, locate your root partition, and delete the /home directory.  Now reboot normally.  If you did everything correctly, you should be using the new partition as your home directory.

---

### Post by ryanhaigh on 2009-03-28
Actually you won't need to delete the /home you are currently using, the new partition will just mount over the top of it. In fact if you did delete the /home directory you would get an error that the mount point doesn't exist.

---

### Post by nicol_bolas on 2009-03-29
> **mb_webguy said:**
> If I'm understanding you correctly, then you have a partition already formatted and sitting there waiting to be used as your home directory, but you forgot to mount it during installation, correct?

If that's the case, then mounting it is only slightly more complicated than... well, mounting it.

First, find out what you need to know to mount it.  Use the command "sudo fdisk -l" to list your partitions, and identify the device listed for the partition you want to use as your home directory.  Write this down or copy it somewhere, so you don't forget.  Now use the command "ls /dev/disk/by-uuid -alh" to identify the UUID (the long alphanumeric string) associated with the drive by cross-checking it with the device number.  Copy the UUID somewhere, since we'll be using it later.

Now mount the partition temporarily with the following commands, substituting the approprate device ID for *xxxn*.  Then copy the contents of your current home directory to the newly mounted partition.```
sudo mkdir /mnt/newhome
sudo mount /dev/*xxxn* /mnt/newhome
sudo cp -r /home /mnt/newhome
```
Now we need to edit the fstab file so the partition will be mounted as home on startup.  Use the command "gksu gedit /etc/fstab" to open the file, then add the following line, substituting the appropriate device ID and UUID for your partition.  (Note that the important thing here is the UUID.  The first line is just a comment to make things easier for you if you want to edit fstab later.)```
# /dev/*xxxn*
UUID=*lots_of_letters_and_numbers* /home           ext3    relatime        0       2

```
Now you only have one problem -- you have two different home directories.  You need to delete the one you don't want anymore, but you can't do that while you're using it.  So boot up a LiveCD, locate your root partition, and delete the /home directory.  Now reboot normally.  If you did everything correctly, you should be using the new partition as your home directory.

This worked minus copying the home folder to my /home partition as all my files were still on there, and only deleting the contents of the home folder as per the post above.

Thank-you all for your help

---

