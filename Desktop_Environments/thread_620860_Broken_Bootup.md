---
title: "Broken Bootup"
date: 2007-11-23
forum: Desktop Environments
---

### Post by DWTebriel on 2007-11-23
Well, I tried to make Linux do the mambo and I guess I broke it.

I am currently running Windows XP SP2 and Ubuntu 7.10, with GRUB as the boot loader. I have three primary partitions, NTFS, EXT3, and FAT32 (document partition).

I went and tried to modify the splash screen with the following process on this site:
[http://www.gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468]("http://www.gnome-look.org/content/show.php/Usplash+Theme+-+Fingerprint?content=50468")

I then proceeded to follow the provided instruction from this site:
[https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765]("https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765")

It has me do a couple of modifications with the following commands after copying the required file to the /usr/lib/usplash directory.
```
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-theme-fingerprint.so 10
sudo update-alternatives --config usplash-artwork.so
sudo update-initramfs -u
```

Well, somewhere along the line something broke an important boot record. Now when I boot under recovery mode in GRUB, it just hangs shortly after trying to boot. The last few lines are as follows (with the ellipses for long UUIDs and other numbers)

```
[6.543738] VFS: Cannot open root device "UUID=..." or unknown-block(0,0)
[6.543800]Please append a correct "root=" boot option; here are the available partitions:
[6.543860] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

Essentially, if it is at all possible, I would *really* like to recover my Ubuntu installation. If that is not possible, then I have to find a way to reinstall Ubuntu over the current installation and not wipe out my Windows XP installation.

I definitely appreciate any help anyone can offer.

---

### Post by athomson on 2007-11-23
Hi,

The "why" is fairly easy, the fix is a bit lengthy. The short answer is that the initrd image was not updated or was updated with an incorrect disk setting.  This can turn into a very long and detailed set of steps. So I will outline what is needed, and then have you boot from the install cdrom to fix it.  If some of the steps in the outline indicate that a file setting is wrong, I will leave it up to you on how to edit the file to fix it :-). So first an  explanation on the steps, then figure out how to get you access to disk to fix it.

The initrd image is located in '/boot' and looks like the line below, the numbers after the key words "initrd.img-xxxxxxxx" will be dependent on what kernel you have installed.  There can be more than one of these initrd.img files. 

```

Example - initrd.img file

  /boot/initrd.img-2.6.22-14-generic

```

Quick Summary

In your case, since grub is loading, and it's loading the kernel, it means that your Grub install is ok.  You did not mention it, but I assume that since Grub is the boot loader, that you also use it to boot to Windows. From the error message that you provided, it appears that Windows is on the first partition, however Ubuntu is on either the second or third partition.  Since you have booted into Windows using Grub, it's also confirmation that Grub is working properly and the issue is likely the initrd.img.  

A Quick Grub Review

Grub creates it's own internal mapping of disk drives.  The format is like this:

  hd( 0, 0 )
  
  The first parameter is the disk drive.
  The second parameter is the disk partition.

All numbering starts at zero [0]. So the first disk drive is [0], the second one is [1] and so forth.  The same applies to partitions, the first partition is [0], the second partition is [1].

In your error message, the last line indicates that the kernel is looking on disk 1, partition 1 for the Ubuntu installation.  "unknown-block(0,0)"

```
 [6.543860] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block[COLOR="Red"](0,0)[/COLOR]
```

How To Fix It

There are two items that need to be checked: 1) the disk that grub is going to boot from, and 2) the partition that it is to use to load Ubuntu.  In your case the first item is correct because windows boots, it's the second one that is wrong, and it's can be wrong in one or two places. 

Verify that the Grub device mapping is correct.  This requires access to the partition where '/boot' exists.  The file is called */boot/grub/device.map*, it's a plain text file that will have one or more lines telling grub what disks is suppose to know about.

```
*/boot/grub/device.map*

[INDENT]For SATA or SCSI it will look like this:

[INDENT](hd0)   /dev/sda[/INDENT]

For IDE

[INDENT](hd0)  /dev/hda[/INDENT]
[/INDENT]
```


There are two locations for the partition that is to be used, one is in the Grub menu, and the other one is in the initrd.img file.  

Here is an example of the Grub Menu file: * /boot/grub/menu.lst*

You are interested in the lines that look like this:

```
title           Ubuntu 7.10, kernel 2.6.22-14-generic
[COLOR="Red"]root            (hd0,1)[/COLOR]
kernel          /vmlinuz-2.6.22-14-generic root=/dev/md1 ro 
initrd          /initrd.img-2.6.22-14-generic

title           Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
[COLOR="Red"]root            (hd0,1)[/COLOR]
kernel          /vmlinuz-2.6.22-14-generic root=/dev/md1 ro single
initrd          /initrd.img-2.6.22-14-generic
```

Your Windows entry will be located at the bottom of the file and will look like this:

```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

The above example is from a system that is using RAID1, so the 'root' is a bit different from yours.  Make sure your 'root' points to the correct partition for your Ubuntu installation.

If your Ubuntu installation is on partition 2, then the root will be '(hd0,1)', if your Ubuntu installation is on partition 3, then the root will be '(hd0,2).  It's repeated here:

```
[INDENT]If root is on the second partition, then 'root hd(0,1)'
If root is on the third partition, then 'root hd(0,2)'[/INDENT]
```

The second location for the partition is in the initrd.img file.  It's just safer to rebuild it then to try to mess with it.

```
update-initramfs -c -k 2.6.22-14-generic
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
```

It's likely that you are doing this from a cdrom boot, so make sure you specify the kernel name.  Do not try something like update-initramfs -c -k `uname -r`, it will just fail and mess up your image.  

---

Okay, so now how to access the disk?  Fastest way is to boot with the install cdrom and let it come up in the Ubuntu GUI. 

Note: Most of the following section was from here, because was I too lazy to type it all in in:  [COLOR="Blue"][https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")[/COLOR]

---
Select Applications>Accessories>Terminal.

Become root

```
sudo -i
```

Now that you have root access, you need to mount the partition(s) containing your bootloader files.

You will need access to both your /sbin/ and /boot/ directories. If you have a /boot/ listing in your fstab, you will need to mount two partitions. In your case this is unlikely because you said you had three partitions, so everything is located on either /dev/hda2 or /dev/hda3.  I  am assuming that /dev/hda2 is your Ubuntu location, if it is not, just replace the '2' with it's correct location.

Create a mount point 

```
mkdir /mnt/work 
```

If you need to mount /boot/, too, run the following command. Again I think all of your data is located on a one partition based on the information you provided, so this step is not needed ... however just to keep Mr Murphy away...

```
mkdir /mnt/work/boot 
```

Now it's time to actually load your filesystem data. Review your fstab and identify the location(s) of / and /boot/; these will likely look something like /dev/hda2 and /dev/hda3, though the letter 'a' and the numbers 2 and 3 may differ.  

Enter the following commands to load your filesystem and some information GRUB may need.

```
mount /dev/hda2 /mnt/work 
mount -o bind /dev /mnt/work/dev
mount -o bind /proc /mnt/work/proc
cp /proc/mounts /mnt/work/etc/mtab
```

Now, you have to enter your working environment. The following command will take care of that.

```
chroot /mnt/work/ /bin/bash 
```

If all of the assumptions I made are correct about your system, and the grub menu.lst file has the correct root (hd0,1) entry, all you need to do is run the update command.

```
update-initramfs -c -k 2.6.22-14-generic
```

Now exit the chroot environment and reboot

```
exit   << exit chroot
reboot  
```

Hopefully this will fix your problem, if not, then post your device.map and menu.lst files and we can figure out what is going on. 

Andy

---

### Post by DWTebriel on 2007-11-25
It worked!!! :)

I greatly appreciate the in depth help you wrote here. I also appreciate the explanation of the problem. And now I don't have to do a reinstall of Linux. I definitely know a bit more about the boot process than I did before.

I don't know how to say how much I appreciate your support. Hope you have a good week!

---

### Post by jken146 on 2007-11-26
I have the same problem, but following your steps didn't work for me.  My thread is at [http://ubuntuforums.org/showthread.php?p=3842060](http://ubuntuforums.org/showthread.php?p=3842060)

---

### Post by wiseguy1515 on 2007-11-26
Thank you so much athomson! I had the same problem [here]("http://ubuntuforums.org/showthread.php?p=3842667") and this fixed it. I'm so glad I found this thread!
Thanks again!

---

### Post by athomson on 2007-11-27
Hi,

Slight correction to the instructions [what I get for being lazy and doing a cut-and-paste instead of typing]

If you have a separate /boot partition you need to mount it after you mount the root partition.

The steps would look like this,

Create a mount point 
```
mkdir /mnt/work
```

Mount the root partition
```
mount /dev/hda2 /work
```

If you have a separate /boot partition, mount it
```
mount /dev/hda1 /boot
```

... then follow the rest of the steps.

Andy

---

### Post by octesian on 2007-11-28
I had the same problem and it worked for me too.  The funny thing is that I actually knew why I was doing what I was doing.  Thanks athomson!

---

### Post by Robert Adornato on 2007-12-17
Hi,

Many thanks athomson!  I had exactly the problem described in this thread, and you provided the solution.  My Gutsy install is back up and running like it never went down.

Rob Adornato

---

### Post by ResumeMan on 2007-12-17
Hi,

I just used this post and wanted to provide my experience.

First, quick context: I'm actually using the gPC with the gOS using the Enlightenment desktop, not regular Ubuntu. It shouldn't, and I think didn't have anything to do with my issue, but I wanted to provide the info.Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

I had recently installed a new internal drive, and had  been fiddling around with UUIDs, along the lines of [this]("https://help.ubuntu.com/community/UsingUUID") page. But nothing that I would think would be a problem.

Then, I rebooted the machine to move it, and all of a sudden it didn't work. Got the "Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)" error.

I booted into a regular Ubuntu live CD and followed the instructions here.  When I got to

```
update-initramfs -c -k 2.6.22-14-generic
```

I got an error similar to "/lib/firmware/2.6.22-14-generic does not exist."

I checked in the mnt/work/lib/firmware directory, and the firmware folder was blank. I went to the regular (i.e. live CD) /lib/firmware directory and there was a folder called 2.6.22-14-generic. So I just copied it onto the hard drive.

And it worked! Damned if I know what happened, but it booted right up and as far as I can tell it's working fine.

Anyway, I don't know if this means anything about anything, but I wanted to report what seems to me to be my very odd experience.

Thanks again, I wasn't looking forward to re-installing! :)

---

### Post by shareMenaPeace on 2007-12-22
THANK YOU!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
lol

ok i posted here
[http://ubuntuforums.org/showthread.php?t=647668](http://ubuntuforums.org/showthread.php?t=647668)

wow :)

thanks

---

### Post by gotlinuxed on 2008-03-19
This thread saved my system. Thank you for writing it!

---

### Post by tommawat on 2008-04-12
Hello athompson,  i want to say so many thanks to you for your post.  this is where i ended up, and also followed your link to the place you copied from...i couldnt get your instructions to work, but this was because i used /dev/sda instead of /dev/sda1 .  i found this in the linked page you got your instructions...i found this in the fstab section (i checked in other sections but they only said /sda.  at any rate, this post has been extremely helpful for me to restore my computer.  thanks so much!!! i really appreciate this!

---

