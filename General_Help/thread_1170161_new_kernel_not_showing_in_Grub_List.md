---
title: "new kernel not showing in Grub List"
date: 2009-05-26
forum: General Help
---

### Post by rompstar on 2009-05-26
I compiled and installed a new kernel, and then run 

raymond@dragonfly:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
findfs: Unable to resolve 'UUID=40afac1d-37d1-4022-920a-5887374cfa4d'
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.29.4-ultimate
Found kernel: /boot/vmlinuz-2.6.28.9-ray
Found kernel: /boot/vmlinuz-2.6.28-12-server
Updating /boot/grub/menu.lst ... done

When I re-boot, I see a reference for an old kernel 2.6.29.11-server and none of these additions are seen ?

I have Ubuntu 9.04

Anyone has any ideas ?

I used the kernelcheck app to auto install last time, saves time this way.

:(

---

### Post by VastOne on 2009-05-26
> **rompstar said:**
> I compiled and installed a new kernel, and then run 

raymond@dragonfly:~$ sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
findfs: Unable to resolve 'UUID=40afac1d-37d1-4022-920a-5887374cfa4d'
Cannot determine root device.  Assuming /dev/hda1
This error is probably caused by an invalid /etc/fstab
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.29.4-ultimate
Found kernel: /boot/vmlinuz-2.6.28.9-ray
Found kernel: /boot/vmlinuz-2.6.28-12-server
Updating /boot/grub/menu.lst ... done

When I re-boot, I see a reference for an old kernel 2.6.29.11-server and none of these additions are seen ?

I have Ubuntu 9.04

Anyone has any ideas ?

I used the kernelcheck app to auto install last time, saves time this way.

:(

Having the same exact issue and did the same exact thing with kernelcheck.  No matter what I do with menu.lst, it saves the edits, but does not show up as a menu item in grub. I thought it was related to a resizing I did of my / filesystem, but now that I see you are having the same issue, I have to rethink this.

---

### Post by rompstar on 2009-05-26
ya, The Grub Menus are all updated and it is still showing the old Menu, I don't understand.  I even reinstalled Grub and Grub Common and still same problem.

---

### Post by Soul-Sing on 2009-05-26
man. adjust the: /boot/grub/menu.lst?
i hope this isn't a uuid problem .....

---

### Post by rompstar on 2009-05-26
Here is what is in my file, this is the paste of all the un-commented lines, everything else is commented out... Is this correct ?

I am not a Grub expert, does something else need to be set in there ?

Also when I do a list:

raymond@dragonfly:/boot/grub$ ls -ls
total 24
4 -rw-r--r-- 1 root root  191 2009-05-17 13:22 default
4 -rw-r--r-- 1 root root   45 2009-05-25 21:05 device.map
8 -rw-r--r-- 1 root root 5174 2009-05-25 21:18 menu.lst

here are all the un-commented lines...

What is that UUID problem you mention ? not an expert ?

menu.lst contents:



default 0
timeout 3
hiddenmenu

title           Ubuntu 9.04, kernel 2.6.29.4-ultimate
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.29.4-ultimate root=/dev/hda1 ro quiet splash $
initrd          /boot/initrd.img-2.6.29.4-ultimate

title           Ubuntu 9.04, kernel 2.6.29.4-ultimate (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.29.4-ultimate root=/dev/hda1 ro  crashkernel=$
initrd          /boot/initrd.img-2.6.29.4-ultimate

title           Ubuntu 9.04, kernel 2.6.28.9-ray
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.28.9-ray root=/dev/hda1 ro quiet splash  cras$
initrd          /boot/initrd.img-2.6.28.9-ray

title           Ubuntu 9.04, kernel 2.6.28.9-ray (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.28.9-ray root=/dev/hda1 ro  crashkernel=384M-$
initrd          /boot/initrd.img-2.6.28.9-ray

title           Ubuntu 9.04, kernel 2.6.28-12-server
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.28-12-server root=/dev/hda1 ro quiet splash  $
initrd          /boot/initrd.img-2.6.28-12-server

title           Ubuntu 9.04, kernel 2.6.28-12-server (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.28-12-server root=/dev/hda1 ro  crashkernel=3$
initrd          /boot/initrd.img-2.6.28-12-server

---

### Post by VastOne on 2009-05-26
> **leoquant said:**
> man. adjust the: /boot/grub/menu.lst?
i hope this isn't a uuid problem .....

I don't know how it could be.  I can edit menu.lst to the moon and back and no matter what i put in there it does not show up in grub at bootup. No matter if I manually change using gedit to select which is the default or fallback or if I use startup manager to make complete changes. My grub is locked into what it was before I ran kernelcheck and it will not change.

I am requesting the help of the author of kernelcheck to assist in that maybe he can at least point something to us, anything now because tho I am no expert, I am not a novice and I am at a loss at to what to try to fix this

---

### Post by rompstar on 2009-05-26
raymond@dragonfly:/dev/disk/by-uuid$ sudo ls -la
total 0
drwxr-xr-x 2 root root 160 2009-05-26 11:17 .
drwxr-xr-x 6 root root 120 2009-05-26 11:17 ..
lrwxrwxrwx 1 root root  10 2009-05-26 11:17 74672c5f-60c3-4e2f-bfd1-53c93d4fcb7e -> ../../sdb2
lrwxrwxrwx 1 root root  24 2009-05-26 11:17 8582189e-4414-415a-8483-1ff76a51ff71 -> ../../mapper/kodiak-root
lrwxrwxrwx 1 root root  10 2009-05-26 11:16 92122c1b-f726-431c-be47-a603f2bb6c25 -> ../../sda1
lrwxrwxrwx 1 root root  10 2009-05-26 11:17 ae65cae3-2fa1-4a1a-be0b-b79e9496b81a -> ../../sdb1
lrwxrwxrwx 1 root root  10 2009-05-26 11:16 be9dbe83-8915-4d4d-81b0-4e7e82ae7a16 -> ../../sda5
lrwxrwxrwx 1 root root  26 2009-05-26 11:17 dc351bb2-3b26-4311-90bd-ae280679b0f3 -> ../../mapper/kodiak-swap_1

/dev/sda1 is my primary IDE drive, that is what has the kernel, the sdb is an external USB drive I use for backup.

---

### Post by rompstar on 2009-05-26
Ok, getting closer, I think this has something to do with the fact that I choose Encryption at install time and Grub can not read encrypted files.

/boot needs to be setup in a un-encrypted partition or something like that.

Just on how to do that, lol

---

### Post by VastOne on 2009-05-26
> **rompstar said:**
> Ok, getting closer, I think this has something to do with the fact that I choose Encryption at install time and Grub can not read encrypted files.

/boot needs to be setup in a un-encrypted partition or something like that.

Just on how to do that, lol

I am not encrypted (to my knowledge) so this may not be the factor

---

### Post by rompstar on 2009-05-26
Ohhh, maybe it is in mine configuration, because I am encrypted, so I am looking into that right now.

---

### Post by unutbu on 2009-05-26
rompstar and VastOne, Would you both run boot_info_script ([http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)) and post the RESULTS.txt? 

VastOne, handling two problems in the same thread can get confusing, so would you please start a new thread and post (or PM me) with the url of the new thread here? This will make it easier on us.

---

### Post by VastOne on 2009-05-26
> **unutbu said:**
> rompstar and VastOne, Would you both run boot_info_script ([http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)) and post the RESULTS.txt? 

VastOne, handling two problems in the same thread can get confusing, so would you please start a new thread and post (or PM me) with the url of the new thread here? This will make it easier on us.

Will do...Tried to "kill" the other part of this thread until this one is resolved...

must paste this as the file exceeds the forums limit on a txt file

but I cant because of this message:

The following errors occurred with your submission:

   1. You have included 12 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

      Images include use of smilies, the BB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.

---

### Post by VastOne on 2009-05-26
> **unutbu said:**
> rompstar and VastOne, Would you both run boot_info_script ([http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)) and post the RESULTS.txt? 

VastOne, handling two problems in the same thread can get confusing, so would you please start a new thread and post (or PM me) with the url of the new thread here? This will make it easier on us.

Trying again

I edited this results file and took out grub data from a secondary disk that I just added to this machine. This shrunk it enough to attach it

---

### Post by VastOne on 2009-05-26
I can clearly see in this results file what is going on but do not understand how it is even possible.  

It goes back to my "other" issue.  /dev/sda1 and /dev/sda8 are supposed to be one and the same from the expansion I did of / in gparted.  In fact, when I look at my root dir it tells me the exact space of those two combined.

But, all the saves I am making to menu.lst is going only to /dev/sda8 but the grub is loading from /dev/sda1

sudo gedit /boot/grub/menu.lst should be saving on sda1 but in fact is saving on sda8

:confused:

Me thinks I am borked!

---

### Post by VastOne on 2009-05-26
This is a snapshot of my partitions and the errors regarding my 2 root partitions

/Dev/sda1 error is:

Warning: Unable to read the contents of the file system!

/Dev/sd8 error is:

Warning:

Unable to find mount point

Unable to read the contents of the file system!

---

### Post by unutbu on 2009-05-26
VastOne, as you have noticed, the problem is that sda1 and sda8 share the same UUID.
Only one of these partitions is getting mounted -- sda1.

We can fix this by changing the UUID of either sda1 or sda8.
sda1 is 4.7GiB and sda8 is 69.1GiB. sda1 is uncomfortably small for a root partition, so I am guessing you wish to use sda8. 

If that is correct, then boot from the LiveCD, and type
```

sudo tune2fs -U random /dev/sda1
```

This will change the UUID of sda1 to a randomly generated UUID.
With any luck it will now be different than any of your other UUIDs.

Next, type

```
sudo grub
root (hd0,7)
setup (hd0)
quit
```

This will change GRUB to boot from sda8 instead of sda1. 
Reboot.

---

### Post by VastOne on 2009-05-26
> **unutbu said:**
> VastOne, as you have noticed, the problem is that sda1 and sda8 share the same UUID.
Only one of these partitions is getting mounted -- sda1.

We can fix this by changing the UUID of either sda1 or sda8.
sda1 is 4.7GiB and sda8 is 69.1GiB. sda1 is uncomfortably small for a root partition, so I am guessing you wish to use sda8. 

If that is correct, then boot from the LiveCD, and type
```

sudo tune2fs -U random /dev/sda1
```

This will change the UUID of sda1 to a randomly generated UUID.
With any luck it will now be different than any of your other UUIDs.

Next, type

```
sudo grub
root (hd0,7)
setup (hd0)
quit
```

This will change GRUB to boot from sda8 instead of sda1. 
Reboot.


unutbu...

Thankee Sai!

I cannot tell you how grateful I am that you took the time to teach some very valuable new tools and the effort to help someone as lost as I was...

I saw this was the case but had very little insight into how to solve it...

You taught me to fish a little better today and for that Thankee Sai!

:D

---

### Post by Greenwidth on 2009-05-27
Hi
Just finished my first kernel compile and got dpkg quit error 100 (?) at 90%+, but everything seems to work fine except, just after GRUB I get:

[    0.890497] cpufreq: No nForce2 chipset.

And then it continues to boot normally, it is quite correct, I don't have nForce2 chipset, I have nForce 680i SLI..

Is it anything to worry about?

---

### Post by rompstar on 2009-05-27
I figured this out by reinstalling Ubuntu 9.04 Server from scratch, this time I choose no encryption.  It was easier to reinstall and restore my key files than to mess with wasting time.

---

### Post by master_kernel on 2009-05-27
So it was encryption?

---

