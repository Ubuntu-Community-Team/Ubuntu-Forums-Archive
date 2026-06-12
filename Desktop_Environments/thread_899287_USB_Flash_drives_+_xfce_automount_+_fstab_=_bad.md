---
title: "USB Flash drives + xfce automount + fstab = bad"
date: 2008-08-24
forum: Desktop Environments
---

### Post by LordSoretor on 2008-08-24
Hello, I finally decided to post this one because it's driving me crazy.

The problem goes like this: I have a 1GB Flash Drive that has an entry on fstab, but since I added the line, XFCE no longer automounts it, because it says it doesn't have the right permissions. The textual message is <Mount Failed: You don't have the right permissions to mount the volume "PEN_MOCHO">.

The line in fstab is
```
LABEL=PEN_MOCHO	/media/PEN_MOCHO	vfat	rw,user,exec,uhelper=hal,shortname=mixed,uid=1000,utf8,fmask=133,dmask=022,flush	0	0
```

That line works fine in Gnome. 

Actually, I've tried changing a lot of mount options (user, users, nousers, gid=0, etc), but just adding the line in fstab makes XFCE unable to auto mount the flash drive altogether, even when the "defaults" options is in, or no options at all.

I also tried to change the permissions of /media with no help.

I guess that if at least someone tells me what kind of permissions XFCE needs, or how it wants to automount, I could do the rest, and learn in the process.

Thanks in advance.

---

### Post by Glw8z on 2008-08-25
I think adding any info on the Flash drive in *fstab* is unnecessary. You should go to Removable Drives and Media in Settings Manager. There in the Storage tab, check the options on mounting removable drives (I have all five checked, and everything works smoothly). That should solve it.

---

### Post by LordSoretor on 2008-08-26
I added the info on fstab because I need the flash drive to be mounted a certain way: with fmask, dmask, iocharset=utf8, etc.

Thanks anyway for your reply.

---

### Post by randcoop on 2008-08-26
You might want to change the fstab reference to the UUID of the drive, rather than using your > LABEL=PEN_MOCHO	/media/PEN_MOCHO

The UUID reference starts the line in fstab with ```
UUID=
``` and then the UUID of the device.

In my experience, fstab does better with the direct UUID.  I would also think that it would eliminate your permissions problems.

You can find the UUID with ```
sudo blkid
``` or ```
sudo vol_id -u /dev/sdb1
``` (obviously using the correct device name for your particular USB drive).

---

### Post by LordSoretor on 2008-08-26
> In my experience, fstab does better with the direct UUID. I would also think that it would eliminate your permissions problems.

I tried the UUID, no dice.

But the way the flash drive is mounted makes no difference, I've tried with /dev/sd*1, with LABEL and with UUID, but it's all the same: the problem seems to be with the XFCE mounting, not with the normal mounting, because I can always mount the drive from a terminal. The thing is that I want XFCE to mount the drive automatically with the options defined in fstab, not to do it myself...

---

### Post by randcoop on 2008-08-27
The problem is not with XFCE in general, because XFCE automatically mounts every flash drive that I use.

In order for that to work, you need to make sure that Thunar volume management is turned on.  In thundar, edit preferences, click on Advanced, and make sure that enable volume management is checked.  That's the mechanism by which XFCE automatically mounts usb flash drives.

If you want the drive mounted at boot, that's when fstab comes into play.  You don't need an fstab entry at all for XFCE to automatically mount the drive.

And if the UUID is not working, I think it's because you're not putting the line in correctly.  An example of a usb drive that I mount using fstab is this: ```
UUID=32BCA4F8CBA4B92D /media/Rock ntfs defaults,utf8 0 0
```

Note that first comes the UUID, then the mount point (you didn't use that order), then the file type (mine is ntfs, yours would be vfat), then the rest.  

So I believe there are a combination of problems.  If you want automatic mounting in XFCE when the drive is inserted, you need to enable volume management in thunar.  If you want that to be in accordance to your settings in fstab, you need to make sure that the line is in the correct sequence.

---

### Post by LordSoretor on 2008-08-27
Sorry, I guess I didn't explain myself very well. The options in fstab are always OK, because I can always mount the flash drive manually.

Let's say I have in fstab
```
LABEL=PEN_MOCHO	/media/PEN_MOCHO	vfat	rw,user,exec,uhelper=hal,shortname=mixed,uid=1000,utf8,fmask=133,dmask=022,flush	0	0
```

With that line, I can always mount the flash either by putting "mount PEN_MOCHO" or "mount /media/PEN_MOCHO". The problem is that XFCE DOESN'T automount it. 

I tried with the Thunar volman on and it says that I don't have permissions to mount that volume when it detects the drive. If I turn off the automount from volman, then the icon of the flash drive appears on the desktop, but isn't mounted. When I double click on it to mount, the "you don't have permissions" message appears.

That's the problem. I need to add the line in fstab because there are some options, like fmask, that I need.

Anyway, I hope someone has a solution for this. It isn't critical but it's quite annoying...

---

### Post by reve_etrange on 2008-08-28
I am experiencing the exact same issue.
In my case there is a SD card perpetually in my laptop, which I want mounted at boot time.

```
UUID=27942ec2-7c62-4a23-8328-61b5ba7ec283	/mnt/matlab2008a	ext2	noatime,rw	0	0
```

I'm certainly not using any special options.  Just tried using UUID instead of /dev/sdb1 - no dice.

---

### Post by randcoop on 2008-08-29
When you run ```
sudo cat /proc/partitions
``` does /dev/sdb1 show up?  The UUID approach to fstab won't work if /proc/partitions hasn't picked up the device.

---

### Post by reve_etrange on 2008-08-30
I take it back - after further rebooting using UUID proved to have worked.

It shouldn't be necessary, though...

---

### Post by randcoop on 2008-08-30
There's a tone to this thread that I don't understand.  The OP was so sure that he was doing everything right that he didn't want to seriously consider that he wasn't.  Then you were quick to report something didn't work when it did.

Now, you're apparently unhappy that it works, but not the way you want...all because you have to use UUID instead of device name.

For what it's worth (and it may not be worth much), the concept behind letting UUID be used instead of the device is that UUID is a permanent identification of the device.  As you probably know, when you plug in a device, it might be assigned a different device name from one episode to the next.  /dev/sdb1 becomes /dev/sdc1 the next time it's plugged in.  But the UUID will always be the same.

I am happy that the automatic boot is working for you.

---

### Post by reve_etrange on 2008-08-30
I'm aware of the purpose of UUID.
Yes, I should have been more thorough before reporting that it didn't work.

It remains odd that on a system with /one/ device other than the boot partition being mounted at boot time UUID must be used in fstab.
It's not behavior I have encountered before.

---

### Post by AlecJ on 2009-04-01
Hi

I have tried both the combinations and am still getting problems with not being privilaged?

I have a 1Tb usb drive named Lacie 1Tb which I think is the problem there is a space in there.

how do i get this to automount on boot up and also I'm getting CD mounting problems.

---

### Post by btittelbach on 2010-07-02
It seems the trick is not to use the UUID in the fstab device field, but whatever xfce-automount uses to identify the device.

For internal devices this will often be the UUID, for SDCards in my internal reader it was the device file itself.

i.e. using the UUID did not work, but

```
/dev/mmcblk0p1 /mnt/sdcard ext4  exec,nosuid,nodev,relatime,auto,user,acl,user_xattr,uhelper=hal 0 0
```

let's me mount the device both with "mount" from the commandline and with thunar.

cheers

---

### Post by Dax0r on 2010-08-07
> **btittelbach said:**
> It seems the trick is not to use the UUID in the fstab device field, but whatever xfce-automount uses to identify the device.


Yes, I think so.
By the way only /dev/sda1 entry works for me. 
Is there no way to make works LABEL entry or UIID entry?

---

### Post by denham2010 on 2010-08-07
As the OP has mentioned, he is able to mount the drive manually, whatever the fstab entry is.

This is a problem with permissions.

If thunar is saying you do not have permission to mount the device, but manually mounting it works (I'm guessing with sudo mount????), I'm guessing you are not a member of the volman group (I think that's what it's called).

Open up Users & Greoups from the System menu and check that you are part of that group.

AlecJ, it could be a similar problem for you with mounting CDs. Make sure you are in the correct group to allow mounting of CDs.

Cheers.

---

### Post by Dax0r on 2010-08-08
It's not that easy.
Manual mount works from normal user, and user's groups are all ok.
Automatic mount works if fstab LABEL (or UIID) is deleted.It works only with /dev/sdaX.
I guess this is an upstream bug...

---

