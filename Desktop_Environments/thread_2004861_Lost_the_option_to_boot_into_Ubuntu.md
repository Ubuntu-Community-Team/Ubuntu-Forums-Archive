---
title: "Lost the option to boot into Ubuntu"
date: 2012-06-16
forum: Desktop Environments
---

### Post by williamcharles on 2012-06-16
I am using ubuntu 11.10 edition dual boot with windows 7..

I was earlier using
/dev/sda5 (/ partition)
/dev/sda6(/boot partition)
/dev/sda8(linux swap)
/dev/sda9 (ext3 logical partition)
Recently i repartitioned one of my local disk, after i rebooted i got 

> 
error: unknown filesystem
grub rescue > 

After searching through the internet, i found out that I need to install boot-repair from live cd which will repair my grub.

I installed boot-repair, followed the instructions but now I have the grub installed..but it only contains the option to boot into windows..my option to boot into linux has been lost.

Any help would be appreciated.

---

### Post by Cavsfan on 2012-06-16
Your fstab UUID entries changed when you repartitioned
Use a live cd, 

First get your UUID for the partitions with **sudo blkid** in terminal.
I open a gedit and past the contents into that for easy copying and pasting.

Then enter

```
sudo mount /dev/sda5 /mnt
```Then enter 
```
gksu gedit /mnt/etc/fstab
```The line above the UUID that is commented out will probably be wrong.
But, enter the UUID from whatever it is to what you got from the sudo blkid command above and save the file.
Then reboot.

---

### Post by williamcharles on 2012-06-16
> **Cavsfan said:**
> Your fstab UUID entries changed when you repartitioned
Use a live cd, 

First get your UUID for the partitions with **sudo blkid** in terminal.
I open a gedit and past the contents into that for easy copying and pasting.

Then enter

```
sudo mount /dev/sda5 /mnt
```Then enter 
```
gksu gedit /mnt/etc/fstab
```The line above the UUID that is commented out will probably be wrong.
But, enter the UUID from whatever it is to what you got from the sudo blkid command above and save the file.
Then reboot.
I tried the method you described...the UUID of my linux drives are still the same...

The drive on which i repartitioned was a ntfs drive..i havent touched the drive on which i had linux installed.

Any more suggestions?

---

### Post by Cavsfan on 2012-06-16
Help is on the way.  I asked a friend to look at this and your problem will be solved.

---

### Post by drs305 on 2012-06-16
Just confirm it is booting from GRUB and not the Windows bootloader?

From the Boot Repair app there is an option to run the boot info script. Please run it and post the link so we can see the status of your system.

---

### Post by williamcharles on 2012-06-16
> **drs305 said:**
> Just confirm it is booting from GRUB and not the Windows bootloader?

From the Boot Repair app there is an option to run the boot info script. Please run it and post the link so we can see the status of your system.

yes..it is booting from grub ..i can see the Grub Version 1.99

---

### Post by williamcharles on 2012-06-16
here is the output from boot-repair

[http://paste.ubuntu.com/1044726/](http://paste.ubuntu.com/1044726/)

I need to fix this asap because all of my development stuff is in there and i have lots of work to do... :(

Any solutions would be appreciated..

---

### Post by Cavsfan on 2012-06-16
Drs305 is probably looking over your boot info script. I wish I could help but, it is a little beyond me at this time.
He will get you fixed up here pretty quick.

---

### Post by drs305 on 2012-06-16
Is your intent to use sda5 as / and sda6 as /boot ? Your sda5 fstab does not include a valid reference to sda6's /boot (it's commented out) and there aren't any kernels in sda5. You have at least 2 options: complete the steps below to reincorporate sda6 as the /boot partition. The other option would be to chroot into sda5 from the same version's LiveCD and install 'linux-image', keeping fstab as it is and removing sda6 from the boot process. For option 2 I have a chroot link in my signature line.

Option 1:

> ======== sda5/etc/fstab: ==
# / was on /dev/sda5 during installation
UUID=9cedbca4-eca2-46a1-9acb-46b9aaa63cea /               ext3    errors=remount-ro,user_xattr 0       1
[COLOR="DarkRed"]# /boot was on /dev/[COLOR="Red"]sda9[/COLOR] during installation
#UUID=172f4dfa-6451-4c66-b3fc-0942a7993f12 /boot           ext3    defaults[COLOR="Red"],exec[/COLOR]        0       2[/COLOR]
# swap was on /dev/sda8 during installation
UUID=143d7957-24c3-48d9-a386-f2ec6a38625e none            swap    sw              0       0

This means that the OS is looking to sda5 for the boot files, but there is no kernel or initrd image in sda5. Also note the contents of fstab comments do not change, and /boot is not on [COLOR="Red"]sda9[/COLOR] as it says.

sda6 has the proper files for booting (kernel, initrd and the grub folder), so if you uncomment the fstab entry for /boot in sda5's fstab. Also add "exec" to the options and save the file. 

grub-install and I think things will work.

So boot the LiveCD, mount /dev/sda5 and edit fstab. Uncomment the /boot line and save the file.
```
sudo mount /dev/sda5 /mnt
sudo mount /dev/sda6 /mnt/boot
gksu gedit /mnt/etc/fstab &
```
Reinstall grub:
```
sudo grub-install --boot-directory=/mnt/boot /dev/sda
```

---

### Post by williamcharles on 2012-06-17
Thanks you drs305, you made my day..it worked and now I can successfully boot into ubuntu...:popcorn:

Now, there is one thing I need to ask you..what steps do I need to perform when I repartitioned/deleted/add a local partition (probably i am going to lose grub once i do it)....please let me know in detail...i will make a point of it....:)

---

### Post by williamcharles on 2012-06-17
Well, now there is one weird thing..I had repartitioned my local partition so that i can use the new partition as ext3 logical partition  on linux..

But now, I dont have permissions on that drive...when i do mkdir, here is what i get...
> mkdir android
mkdir: cannot create directory `android': Permission denied

---

### Post by drs305 on 2012-06-17
In answer to your last two posts: If you want to add a partition, you must make a partition and can add it to fstab.

To create the *android* mountpoint, use the "sudo" command to allow you to run as root. Example (it doesn't have to be on /mnt and doesn't have to be called android):
```
sudo mkdir /mnt/android
```
To make yoursel the owner of the mountpoint (*your username*):
```
sudo chown -R *williamcharles:* /mnt/android
```
Finally, you can add it to fstab:
```

sudo blkid # Gets the partition UUIDs, needed for the fstab entry
gksu gedit /etc/fstab # Opens fstab for editing as root
```
Add the following line, using the UUID for the *android* partition:
```
UUID=<someUUID> /mnt/android ext3 defaults,users 0 2
```
The components of the fstab line are:
UUID of the partition
Mountpoint (whatever you created)
Partition format (ext3, ext4, ntfs, etc)
Options: 'users' allows users to mount the partition. 'defaults' should automount the partition, if not, use 'auto'. 
The final number is to allow periodic fsck checks, at a lower priority than the main system partition.

For more on fstab, see:
[https://help.ubuntu.com/community/Fstab]("https://help.ubuntu.com/community/Fstab")

Save the file and see if the entry is correct:
```
sudo mount -a
```
This command will try to mount all entries in fstab. If your entry is correct, there will be no feedback and the partition is now mounted.

---

### Post by YannBuntu on 2012-06-19
(Hi. For information Boot-Repair should have not commented /boot in fstab. This bug is now fixed in its PPA.)

---

