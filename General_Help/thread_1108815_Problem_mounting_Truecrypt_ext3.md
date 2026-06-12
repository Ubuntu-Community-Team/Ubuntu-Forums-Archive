---
title: "Problem mounting Truecrypt ext3"
date: 2009-03-28
forum: General Help
---

### Post by df9517 on 2009-03-28
Just installed Jaunty Jackalope beta with ext4 file system.

When I try to mount my ext3 encrypted partition on external hdd i get fault message saying I need to specify filesystem.

I then try command line as follows:

sudo truecrypt --filesystem=ext3 /dev/sdc1 /media/truecrypt

Then I get fault message:

device-mapper: create ioctl failed: Device or resource busy

Please, does anyone no why this happened and how I can fix it. I really need those files soon! I googled but no luck.

---

### Post by antiplex on 2009-04-14
hi df9517,

this might be a bit late, but nevertheless:

i run 9.04b 64bit as well on ext4 with truecrypt 6.1a (which is the latest release) and don't have any problem with mounting/accessing truecrypt-encrypted partitions containing ext3 filesystems.
note that my tc-partitions were created with a tc-version after 5.1, so i don't get any 'mode-of-operation' warnings.
i also tried a container containing an ext3 filesystem created with tc 4.1 (old mode of operation, not xts) which worked fine as well.

but while trying around various parameters i came across the message you posted (Device or resource busy) and could not mount the device until i rebooted the system (umount said that the device isn't mounted).

this happened after i got an error while fiddling around with the tc-parameters '--fs-options=' and '--filesystem=' and as far as i remember the error came from mount which gets called by truecrypt and read something like 'wrong fs-type [blahblah]'.
calling 'dmesg | tail' mentioned something about an unknown parameter uuid=1000 as far as i recall.

it seemed that a reboot is necessary if one comes to this scenario.


are you sure /dev/sdc1 is your encrypted partition with an ext3 fs?
maybe you should try to let tc open the partition without mounting it by executing 'truecrypt -t --filesystem=none /dev/sdc1' and then take a look at what 'sudo tune2fs -l /dev/mapper/truecrypt1 | grep features' prints out. ext3 filesystems typically show 'has_journal resize_inode dir_index filetype needs_recovery sparse_super large_file' while ext4 would typically show 'has_journal ext_attr resize_inode dir_index filetype extent flex_bg sparse_super large_file huge_file uninit_bg dir_nlink extra_isize'.

if everything looks like sdc1 is indeed an ext3 partition try to manually mount /dev/mapper/truecrypt1 to wherever you want by executing 'sudo mount -v -t ext3 /dev/mapper/truecrypt1 /media/truecrypt'.
i'm absolutely not sure but i suspect truecrypt internally calling mount with some parameter that somehow doesn't work on systems with ext4 support.

hope this helps; regards,
anti

---

### Post by df9517 on 2009-04-14
I thank you very much for your thorough answer but I gave up some days ago, reformatting the partition. I actually formatted it to FAT32, encrypted it again, and then formatted to ext4 with success (even if truecrypt dont support ext4 it works). After that I could mount and unmount perfectly with truecrypt in my ext4 environment.

I am not sure what went wrong but I strongly think it has to do with mounting on ext4 system.

Again, thanks and hopefully it will help someone else.

---

### Post by evermind on 2009-04-28
I had a similar problem so while searching for the answer I came across this thread. I found out that

```
cryptsetup remove /dev/mapper/truecrypt1
```

removed that busy message for me
```
device-mapper: create ioctl failed: Device or resource busy
```

---

### Post by aavaliani on 2009-04-29
sudo cryptsetup -v remove /dev/mapper/truecrypt1_1  

This will do the job. And then you can use truecrypt again. 

This error happens if you try at least once run Truecrypt with mount point that doesn't exist. After this you will need to first remove the busy device.

Regards,
Archie

---

### Post by djbon2112 on 2009-06-02
I was having this error, so I ran the cryptseup fix, but it says this:

```
joshua@W01-Zeus:~$ sudo cryptsetup remove /dev/mapper/truecrypt1
[sudo] password for joshua: 
Command failed: dm_task_set_name: Device /dev/mapper/truecrypt1 not found
```

and /dev/mapper/truecrypt1 doesn't exist.

But now, I'm getting this:

```
Input/output error:
/dev/mapper/truecrypt1

The drive is damaged (there is a physical defect on it) or a cable is damaged, or the memory is malfunctioning.

Please note that this is a problem with your hardware, not with TrueCrypt. Therefore, please do NOT report this as a bug/problem in TrueCrypt and please do NOT ask for help with this in the TrueCrypt Forums. Please contact your computer vendor's technical support team for assistance. Thank you.

Note: If the error occurs repeatedly at the same place, it is very likely caused by a bad disk block, which should be possible to correct using third-party software (note that, in many cases, the 'chkdsk /r' command cannot correct it because it works only at the filesystem level; in some cases, the 'chkdsk' tool cannot even detect it).
```

I just installed Truecrypt via the .deb package on its site, on a fresh install of Ubuntu 9.04 x86_64. Yes, I'm sure I used the 64-bit package.

EDIT: And now, it works. I guess I just needed a reboot!

---

### Post by CDrewing on 2009-08-31
Has anybody a solution yet? I am having the same problem on my network drive. The container can be mounted read-only and I can copy it to my local HD, can mount it there with full access and I can copy it back to the NAS drive.

Hard stuff with 10 GB containers ;-/

My local HD is running on ext4, the NAS is running on ext3.

_edit:_ When I try the "cryptosetup thing" it says 'device not found' with the container being unmounted, or it says 'device busy' with the countainer mounted.

Best regards
Christian


[IMG]http://img408.imageshack.us/img408/9802/bildschirmfototruecrypt.png[/IMG]

---

### Post by djbon2112 on 2009-09-23
Ironically I am also having problems again!

My setup is as follows:

Fileserver contains crypt > mounted locally > accessed by truecrypt

The issues started a few days ago when, attempting to mount the crypt, I got this error:

```
Mount: you must specify a filesystem type"
```

I ignored this until tonight, when I needed to access the volume. I started by running a check on the enabled (but not mounted) volume. It is formatted with ext3. The check returned no errors. I then tried to mount it with the command line, but I got:

```
device-mapper: create ioctl failed: Device or resource busy
``` 

However, after trying again with the GUI, I got the same message I did before, and that CDrewing is having.

I tried the /dev/mapper config commands, but I got the "not found" issue. I access the file over the network, but I've effectively ruled that out as this is the only situation I have problems with, when I regularity and smoothly stream various media and files from this server.

I'm a little frustrated at this right now. I really don't want to lose the data! Suggestions?

---

### Post by CDrewing on 2009-09-23
We should submit this as a bug at the truecrypt homepage, don't you think?

---

### Post by Panna-cakkhu on 2011-03-23
Here is a solution which worked for me:

Go to Setting > Preferences > System Integration > Kernel Services and check the box "Do not use kernel cryptographic services"

Note: you need to do that before your volume is mounted. If it is already mounted you may have to make sure no process is accessing your volume and restart your system.

---

### Post by pacharanero on 2012-10-31
+1 thanks for the above post, which worked

ticking the "do not use kernel cryptographic services" option worked for me

[Xubuntu 12.04.1 LTS, using TrueCrypt 7.1a to access an encrypted volume]


--pach

---

