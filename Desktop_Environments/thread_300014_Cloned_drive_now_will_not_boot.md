---
title: "Cloned drive now will not boot"
date: 2006-11-15
forum: Desktop Environments
---

### Post by leona on 2006-11-15
Hi

Ok some background to my problem.

I wanted to install a new hard disk, my old HDD IDE was full, so got a shiny new SATA drive.

I installed the drive and got windows to see it, installed the sata drivers and all that and after a bit of fidding (and plugging it into the 'correct' header Dam RAID stuff!) got it working.

Norton Ghost 2003 wouldn't touch my linux partitions so I used Ghost 4 Linux as the cool how to's on here suggested.

After G4l had finished (it took a really long time), everything seemed ok, no errors displayed all looked good.

So I unplug my old drive and booted, grub came up, that's a good start I thought, tested Windows, yep that worked fine, rebooted and choose Ubuntu, wouldn't boot, tried again with recovery option gets as far as checking the USB flash card drive, then dumps out.  I initially thought it was the flash card drive at fault, but then I looked at the error.
/dev/hda9 doesn't exsist, dropping to shell.

Oh $h1t!

Booted live cd, which seemed to confirmed that I have no partition pointer '/usr', '/', '/boot' though the actual partitions are there.

Tried to manually mount them, but could only see partial data.

Ok so where do I go from here, can I recover from this point or do I start again?

I think the problem is that I've gone from an IDE drive to a SATA, HDA to SDA. I didn't realise tht Linux would treat them differntly, (or I nievly assumed it would 'cope' with the change).

I suppose I could create blank paritions and copy the data using the old drive in a usb caddy, at last resort.

Any help / suggestions?

Thanks

Leona

---

### Post by RaisedFist on 2006-11-15
First of all, your SATA drive will be /dev/sda (or sdb), so there's no way for Linux to boot from /dev/hda9.

The best way to resolve this is to boot from you live CD, check the new partition on your SATA drive, mount it and set it in /*mountpoint*/boot/grub.conf and /*mountpoint*/etc/fstab.

---

### Post by leona on 2006-11-15
Hi

Thanks for that, yes I thought about doing that, I booted my Ubuntu Live cd and tried to mount the partitions, but where the /boot and /etc used to be it now outputs ? 'uknown' ??? worrying :( ? so I can't access them.  Could it have been the way I mounted it?

---

### Post by leona on 2006-11-15
Any other thoughts anyone??? do I need to mount them using a special command ?

Ok I have the source drive mounted in a usb caddy.  How do I copy the partition over while maintaining all the correct permissions, I have a feeling if I copy it it'll reset everything to root.

---

### Post by dpm on 2006-11-15
I think what you could do is:

1.- Boot from the live cd, open a terminal and type:

```
sudo fdisk -l
```there you should be able to find out what the device name of your sata drive is (it should be something like /dev/sda* or /dev/sdb*. Note it down. Even better, post it on this thread so other people can help you.

2.- Again on the terminal, try to mount your old partition somewhere (it does not matter where, this is only temporary. Note: substitute the asterisk in /dev/sd* for the right device name (the one you noted down in step 1):
```

cd /media
sudo mkdir ubuntu
sudo mount /dev/sd* /media/ubuntu
```If everything worked, you should now have access to your old files under /media/ubuntu. Try to navigate through the folders with nautilus.

3. Now you should modify your grub configuration so the kernel can be loaded from the right partition. Type:

```
sudo nano /media/ubuntu/boot/grub/menu.lst
```and change the line that says something like

```
root  (hd0,8)
```to your current root. I'm guessing 'root sd(0,8)', but you'll have to find out yourself

4. Finally, you'll have to modify your /etc/fstab to mount the right partition at boot:

```
sudo nano /media/ubuntu/etc/fstab
```and substitute /dev/hda9 on the line that looks more or less than this:

```
/dev/hda9 / ext3 defaults,errors=remount-ro
```by your /dev/sd* device

After you've saved the changes to these two files, and rebooted, your ubuntu partition should work as usual.

> I think the problem is that I've gone from an IDE drive to a SATA, HDA to SDA. I didn't realise tht Linux would treat them differntly, (or I nievly assumed it would 'cope' with the change).Yes, Linux names them differently -although I've heard rumours that there are plans to change this soon. If you want to be independent of device names, you could use UUIDs for partitions instead of device names (it is the default in Edgy, BTW).

I hope this helps.

---

### Post by leona on 2006-11-15
HI, Thanks desp that's cleared a lot of things up.

Yep I'm manged to mount the partition and 2 of the 3 look fine, sda7 and 8 but 9 is giving me 'issues'.

Ok the partition that's causing the most problem is sda9 (formally hda9).
```

sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1275    10241406    c  W95 FAT32 (LBA)
/dev/sda2            1276       14593   106976835    f  W95 Ext'd (LBA)
/dev/sda5            1276        8855    60886318+   b  W95 FAT32
/dev/sda6            8856       12043    25607578+   b  W95 FAT32
/dev/sda7           12044       12049       48163+  83  Linux
/dev/sda8           12050       13069     8193118+  83  Linux
/dev/sda9           13070       14338    10193211   83  Linux
/dev/sda10          14339       14593     2048256   82  Linux swap / Solaris

```

But the problem I have is that I can not access the /etc dir on it I get.

```

root@ubuntu:/mnt/sdd9# ls -l
total 88
drwxr-xr-x  2 root root  4096 2006-10-06 17:45 bin
?---------  ? ?    ?        ?                ? boot
lrwxrwxrwx  1 root root    11 2006-09-09 20:49 cdrom -> media/cdrom
?---------  ? ?    ?        ?                ? dev
?---------  ? ?    ?        ?                ? etc
drwxr-xr-x  3 root root  4096 2006-09-09 20:59 home
drwxr-xr-x  2 root root  4096 2006-08-05 23:19 initrd

```
```

root@ubuntu:/mnt# cd sdd9
root@ubuntu:/mnt/sdd9# cd etc
bash: cd: etc: Input/output error
root@ubuntu:/mnt/sdd9#

```
So should my menu.lst look like this?
from [old]
```

title           Ubuntu, kernel 2.6.15-27-amd64-generic
root            (hd0,6)
kernel          /vmlinuz-2.6.15-27-amd64-generic root=/dev/hda9 ro quiet splash
initrd          /initrd.img-2.6.15-27-amd64-generic
savedefault
boot

```
to [new]
```

title           Ubuntu, kernel 2.6.15-27-amd64-generic
root            **(sd0,6)**
kernel          /vmlinuz-2.6.15-27-amd64-generic root=/dev/**sda9** ro quiet splash
initrd          /initrd.img-2.6.15-27-amd64-generic
savedefault
boot

```

---

### Post by leona on 2006-11-15
Any more ideas, anyone? I'm at a loss here.

---

### Post by dpm on 2006-11-16
[LEFT]Hmm... this does not look too good. The permissions on /etc not being shown is a bit weird.

How did you get to that prompt?
```
 root@ubuntu:/mnt/sdd9#
```

The menu.lst changes seem fine to me.

1. A question, though: I see your /boot directory has also got ? permissions, but you seem to have been able to access it to modify /boot/grub/menu.lst. Is that right?

2. Could you post your old fstab from the source hard drive?

3. What happens now when you boot your "Ubuntu, kernel 2.6.15-27-amd64-generic" from grub?

If everything else fails, I would try downloading the GParted livecd ISO ([http://gparted.sourceforge.net/livecd.php)]("http://gparted.sourceforge.net/livecd.php%29"), boot from it, delete the new /dev/sda9 partition and copy it again from the source to the target location. But then make sure to note down the /dev/sd* name of the new partition (it could be that GParted changes it from /dev/sda9 to something else, but then you would only have to update your etc/fstab and /boot/grub/menu.lst accordingly once more).
[/LEFT]

---

### Post by leona on 2006-11-16
Hi desp

Thanks again for your reply.

yes it is very odd, chatting to a few colleagues at work they seem to think there is some kind of corruption and said to run 'fsck' on it to see what the problem might be.

To get that prompt, I created a directory in /mnt called sdd9 I then used mount /dev/sda9 /mnt/sdd9 (a bit of guess work here) and it seemed to work, well it worked for sdd7 and 8.

Yes I have split my partitions up /boot /usr and / (/usr should have been /home, but I was 1/2 asleep when I did it, :) something I'll have to fix at a later date ).

/boot is on /dev/sda7 (/mnt/sdd7) and I'm able to mount that which is how I managed to edit the menu.lst file, I've not attempted a boot yet.

---

### Post by dpm on 2006-11-16
> **leona said:**
> 
To get that prompt, I created a directory in /mnt called sdd9 I then used mount /dev/sda9 /mnt/sdd9 (a bit of guess work here) and it seemed to work, well it worked for sdd7 and 8.

I meant how did you get to 
```
 root@ubuntu
```did you boot from a live cd or is that after booting from the hard drive and logging in as root?

> **leona said:**
> Yes I have split my partitions up /boot /usr and / (/usr should have been /home, but I was 1/2 asleep when I did it, :) something I'll have to fix at a later date ).

Blimey, this is getting more and more confusing. Unless you post your old fstab, I don't think I can help you further.

> **leona said:**
>  /boot is on /dev/sda7 (/mnt/sdd7) and I'm able to mount that which is how I managed to edit the menu.lst file, I've not attempted a boot yet.
So does that mean you haven't turned your computer off since you started having this problem?

Cheers

---

### Post by leona on 2006-11-16
hi desp

oh dear, I think I caused a bit of confusion here, hum lets see if I can clear some of it up.
> **desp said:**
> I meant how did you get to 
```
 root@ubuntu
```did you boot from a live cd or is that after booting from the hard drive and logging in as root?

You where right, I booted from a live cd, everything I've done since I installed my hard drive has been done from the Live Cd, appart from the first couple of failed boot attempts. Booted from Live Cd, changed the root password (don't know what it gives you as default) then su'd to root.

Oh ya the computer has been off, I just have to set up the mounts each time I boot, bit of a pain but hey.

Don't worry too much about my partitions, they are like that on the source disk, I've not changed them, yet!

Just got home, so I'm going to boot, setup the mounts and run that disk check.

-- added:  That confirmed it really, loads of Inode errors, and after the fix, half the stuff is gone, I think I may have to try copying it again, something must have gone wrong with the ghosting processes.

---

### Post by leona on 2006-11-16
Hi

I've tried to boot the drive, after clearing the faulty partition and copying everything over again.  Made the changes to menu.lst and fstab, but when I boot now I get

[quote=my boot screen]
root sd0,6
Error 23: Error while parsing number
[/quote]

here is what I've put in the menu.lst file
title           Ubuntu, kernel 2.6.15-27-amd64-generic
root            (sd0,6)
kernel          /vmlinuz-2.6.15-27-amd64-generic root=/dev/sda9 ro quiet splash
initrd          /initrd.img-2.6.15-27-amd64-generic
savedefault
boot

---

### Post by leona on 2006-11-16
Arr, silly me, think I spotted my error, got carried away with replacing hd with sd, too much find / replace :) 
root (sd0,6) 
now restored to
root (hd0,6)

and hurrey! after 2 days of faffing about I finally have my system on my new hard drive, I'm sure it wasn't ever this hard with Windows :(

ya lives and you learns......
Again thanks to desp for pointing me in the right direction, much appriecated...

---

