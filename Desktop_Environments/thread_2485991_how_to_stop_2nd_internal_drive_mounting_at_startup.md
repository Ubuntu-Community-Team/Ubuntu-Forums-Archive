---
title: "how to stop 2nd internal drive mounting at startup?"
date: 2023-04-16
forum: Desktop Environments
---

### Post by watchpocket on 2023-04-16
My main working system (Ubuntu MATE 20.04) is on an internal nvme drive on a desktop workstation. 

 I also have Ubuntu MATE 20.04 (as a secondary system) on an internal SSD.  

When I boot up, the SSD auto-mounts on the desktop, and I have to manually unmount it.

How can I prevent the SSD from mounting at startup?  I only want it to be manually mounted.

I realize this may have to do with how my GRUB is set up, but have no clue beyond that about where to begin.

---

### Post by #&amp;thj^% on 2023-04-16
usually to stop auto-mounting of specific devices, add an entry to /etc/fstab with the noauto optiion. (You already know that): [https://ubuntu-mate.community/t/my-2nd-os-drive-auto-mounts-at-login-of-main-install/25071](https://ubuntu-mate.community/t/my-2nd-os-drive-auto-mounts-at-login-of-main-install/25071)
Second is rather harsh, but...
Check:
```
systemctl status udisks2.service 
&#9679; udisks2.service - Disk Manager
     Loaded: loaded (/lib/systemd/system/udisks2.service; enabled; preset: enab>
     Active: active (running) since Sun 2023-04-16 14:08:41 MDT; 1h 2min ago
       Docs: man:udisks(8)
   Main PID: 3223 (udisksd)
      Tasks: 6 (limit: 9067)
     Memory: 7.2M
        CPU: 328ms
     CGroup: /system.slice/udisks2.service
             &#9492;&#9472;3223 /usr/libexec/udisks2/udisksd

```
When I don't want a drive to mount *I'll*  use:
```
systemctl stop udisks2.service
```
That will stop auto mountings.
Or Even:
```
systemctl mask udisks2.service 
```
**_Know this>>>**gnome-disks** stops working, too._**

---

### Post by watchpocket on 2023-04-17
> **1fallen said:**
> usually to stop auto-mounting of specific devices, add an entry to /etc/fstab with the noauto optiion.

That's why I don't understand why this line in my /etc/fstab ***doesn't*** stop the auto-mounting of my internal SSD drive:
```
UUID=21697ef7-83e3-4414-a859-91841f61dce8   /media/rj/20.04-ssd/     ext4   noauto     0     0
```

> (You already know that): [https://ubuntu-mate.community/t/my-2nd-os-drive-auto-mounts-at-login-of-main-install/25071 ]("https://ubuntu-mate.community/t/my-2nd-os-drive-auto-mounts-at-login-of-main-install/25071")


I knew I'd posted about this awhile ago but forgot where & when exactly. Thanks for digging it up.
[COLOR=#0000ff]*systemctl status udisks2.service* [/COLOR]shows:[COLOR=#0000ff][/COLOR]
```
&#9679; udisks2.service - Disk Manager
     Loaded: loaded (/lib/systemd/system/udisks2.service; enabled; vendor preset: enabled)
     Active: active (running) since Mon 2023-04-17 19:16:44 EDT; 13min ago
       Docs: man:udisks(8)
   Main PID: 1282 (udisksd)
      Tasks: 5 (limit: 154309)
     Memory: 15.2M
     CGroup: /system.slice/udisks2.service
             &#9492;&#9472;1282 /usr/lib/udisks2/udisksd

Apr 17 19:16:43 rjbox systemd[1]: Starting Disk Manager...
Apr 17 19:16:43 rjbox udisksd[1282]: udisks daemon version 2.8.4 starting
Apr 17 19:16:44 rjbox systemd[1]: Started Disk Manager.
Apr 17 19:16:44 rjbox udisksd[1282]: Acquired the name org.freedesktop.UDisks2 on the system message bus
Apr 17 19:16:50 rjbox udisksd[1282]: Mounted /dev/sda2 (system) at /media/rj/20.04-ssd/ on behalf of uid 1000
Apr 17 19:16:56 rjbox udisksd[1282]: Cleaning up mount point /media/rj/20.04-ssd (device 8:2 is not mounted)
Apr 17 19:16:56 rjbox udisksd[1282]: Unmounted /dev/sda2 on behalf of uid 1000
```

And yes, [COLOR=#0000ff]*systemctl stop udisks2.service *[/COLOR]stops ***all ***drives from auto-mounting, but I only want to stop ***one*** drive from auto-mounting.
 
And [COLOR=#0000ff]*systemctl mask udisks2.service*[/COLOR] is a bit drastic for my purposes. 

*** My question, really, is why the fstab line won't work.***  Thanks.

---

### Post by aljames2 on 2023-04-17
In addition to the fstab entry you have which is supposed to prevent  automounting at startup or when mount -a is invoked, you could look into  the MATE environment settings.

Our desktops have a way of trying  to make life easy for the average user, so that when something is  plugged in, it just works.  It assumes we want to start browsing.  I  realize your media is internally attached.  So is mine, 500GB Samsung  SSD, just sitting there for some extra storage purposes with data on it.

I am not  that familiar with the MATE DE but you could check under File  Management settings, under the Media tab and fiddle with the other media  options to try to control this behavior.  Perhaps there is another  setting somewhere.  I have read that dconf editor in Gnome is handy.

My daily driver is Xubuntu these days.  I had the same problem you have (I think).  I have the fstab entry but also have under:
Settings - Settings Editor - thunar-volman - and uncheck to set automount-drives to false.  But that's Xubuntu.

Previous  to using this Xubuntu setting for me, my SSD was not automounting at  bootup which was good.  However, when I started a VM that has "read  only" access to the same SSD... upon closing that VM, my host would then  automount the SSD.  I can control this DE behavior in Xubuntu.

---

### Post by #&amp;thj^% on 2023-04-19
> **watchpocket said:**
> 
*** My question, really, is why the fstab line won't work.***  Thanks.
Do you still have Timeshift installed? That will cause a drive to auto mount.
You will see something like Successfully Mounted Drive, and Successfully unmounted Drive.

---

### Post by TheFu on 2023-04-19
You can purge the udisk* off the system. It isn't necessary.

While you are at it, it is best not to mount stuff in the fstab under /media/{username}, since other daemons want to control that location.  Mount it anywhere else and the fstab will be honored.
Lastly, if you add a nice label to the file system (gparted), then the mount location and use LABEL= instead of UUID= and mounting it to /media/{LABEL} will make more sense.  Just don't make the label something common like "Data".  Call it something else, think unique.

---

### Post by watchpocket on 2023-04-20
@aljames2: 
Thank you for those suggestions - I did closely peruse through and try to get the File Management media settings as well as dconf Editor set up to prevent the automount of the SSD in question, with no luck.

@1fallen: 
I do still use Timeshift, but I have the snapshot location set to an external SSD that's always USB-unplugged; I plug it in only when I want to do a system backup (about once a week), then unplug it again.  So far at least, I tend towards Timeshift not being an interfering factor.

@TheFu: 
In gparted I gave /dev/sda2 ( /dev/sda is the internal SSD that I want to stop from automounting) a file-system Label of "**20.04-ssd**" and a partition name of "**UbuntuMATE-20.04-ssd**". 

And I've created a directory named */media/20.04-ssd/*  
( In addition to the already-present */media/USB/* and [I]/media/rj/ ) .

[/I]And in* /etc/fstab *I put this line:
```
LABEL=20.04-ssd   /media/20.04-ssd/     ext4    noauto    0       0
```

and I wonder if I'm correclty doing what you sugested, since when I re-booted, the 20.04-ssd still auto-mounted onto the desktop.  
(see screenshot)

(I haven't purged udisks2 just yet - hope that isn't causing a problem.)

Btw, I have a 2nd internal SSD -- there's no OS on it, it's a storage drive -- and it doesn't auto-mount. 
 (When I mount it manually, it mounts to /media/rj/ )
So I wonder why the SSD w/ the OS on it auto-mounts?

---

### Post by #&amp;thj^% on 2023-04-20
I'll use something like this for fstab:
```
UUID=86155041-8680-4914-9b01-9c50f9aaf7aa /storage      ext4   defaults,noatime,noauto,user             0  0
```
Not sure it will make a difference with your or not, With "noauto,user", any regular user will be able to mount and unmount the drive he/they needs.

---

### Post by TheFu on 2023-04-20
I'd use:
```
LABEL="20.04-ssd"   /media/20.04-ssd     ext4    nofail,noauto    0       2
```

But really I wouldn't use odd characters in the label.

According to the mount manpage, ```

       noauto Can only be mounted explicitly (i.e., the  -a  option  will  not
              cause the filesystem to be mounted).

```
If it is being mounted by some other tool, then the issue lies with that tool and you'll need to clean it up there.  i.e. purge udisk*

---

### Post by watchpocket on 2023-04-20
TheFu said:
>* But really I wouldn't use odd characters in the label.*

So I should remove the dot and the hyphen?

---

### Post by TheFu on 2023-04-20
> **watchpocket said:**
> > But really I wouldn't use odd characters in the label.

So the odd characters are dot and hyphen?

When things aren't working as expected, suspect stupid things.  Yes?

I recall 25 yrs ago when I didn't leave an empty line at the bottom of config files and the last line in the config wasn't being seen.  Computers think EOF and EOL are different. The programmer for that config file never though someone would have an EOF on the same line as a config option.  Dumb, stupid things.  Since that time, I've always had 1 blank line at the bottom of every config file to avoid stupid issues that can eat up days.

---

### Post by watchpocket on 2023-04-20
TheFu said: 
> [I]You can purge the udisk* off the system. It isn't necessary.

[/I]Marking udisks2 for removal indicates that a whole lot of other things  would also be removed like gnome-disk-utility, ubuntu-mate-desktop,  ubuntu-mate-core and caja.   *So, brrrrrrrrrrrrr,* I don't know about that.

TheFu said:
>[I] But really I wouldn't use odd characters in the label.

[/I]So I should remove the dot and the hyphen.  Done.

1fallen wrote[I]:
> /storage

[/I]Except that this SSD contains an OS.  But I guess the point is to mount it directly off / and not in /media?

---

### Post by TheFu on 2023-04-20
> **watchpocket said:**
> TheFu said: 
> [I]You can purge the udisk* off the system. It isn't necessary.

[/I]Marking udisks2 for removal indicates that a whole lot of other things  would also be removed like gnome-disk-utility, ubuntu-mate-desktop,  ubuntu-mate-core and caja.   *So, brrrrrrrrrrrrr,* I don't know about that.

TheFu said:
>[I] But really I wouldn't use odd characters in the label.

[/I]So I should remove the dot and the hyphen.  Done.

1fallen wrote[I]:
> /storage

[/I]Except that this SSD contains an OS.  But I guess the point is to mount it directly off / and not in /media?

Mounts are per file system, not per storage device.
I don't mount any extra storage under /media.  I mount things under /d/.  Not exactly magical, but here's some examples on a media and backup server:
```
Type  Size  Used Avail Use% Mounted on
ext4  3.6T  3.5T  140G  97% /d/b-D1
ext4  3.6T  3.6T   27G 100% /d/b-D2
ext4  3.6T  3.6T   79G  98% /d/b-D3
ext4  3.6T  211G  3.2T   7% /d/b-D6
ext4  3.4T  600G  2.7T  19% /d/b-D7
ext4  3.5T  3.5T   34G 100% /d/D1
ext4  3.6T  3.6T   23G 100% /d/D2
ext4  3.6T  3.6T   74G  98% /d/D3
ext4  3.6T  211G  3.2T   7% /d/D6
ext4  3.6T  599G  2.9T  18% /d/D7
ext4   26G  9.9G   15G  41% /home

```
The /d/D* are primary storage.
The /d/b-* are for backups.

Note that D4 and D5 are missing?  I've had some drive failures and shuffled some mounts around.  Additionally, I use tune2fs to reduce the reserved blocks for root-only use on all these 'data' areas to zero.  Normally 5% of the file system space is reserved for use by root.  On multi-terabyte disks, that's a huge amount of storage.  For file systems holding important OS stuff, 5% is a good idea. Elsewhere, perhaps, not such a good idea. YMMV.

---

### Post by Dennis N on 2023-04-20
> Marking udisks2 for removal indicates that a whole lot of other things would also be removed like gnome-disk-utility, ubuntu-mate-desktop, ubuntu-mate-core and caja. So, brrrrrrrrrrrrr, I don't know about that.

udisks2 is the 'helper' that mounts USB drives when they are inserted (as shown is the display below). So I would not remove it. 
```
dmn@kayleigh ~]$ mount | grep udisks2
/dev/sda1 on /media/dmn/MyData type ext4 (rw,nosuid,nodev,relatime,seclabel,errors=remount-ro,[COLOR="#FF0000"]uhelper=udisks2[/COLOR])

```
Here, sda is a USB flash drive.
comments:
I've not seen any internal disks just get mounted without user action if there is no fstab entry to mount it, at least in the Gnome Desktop.
I mount my separate data partition using a subdirectory of /mnt for the mount point.

---

### Post by watchpocket on 2023-04-23
I'm wondering if the following might help me track this problem down:  

When I log into my SSD drive's UbuntuMATE 20.04 --

(This is the SSD drive that is my backup OS, and the one that's in question here for auto-mounting --  which I don't want it to do -- when I log into my main (nvme) drive.

When I log into that SSD, my nvme drive DOES NOT auto-mount at login.

In other words, the OS drive (the SSD) that I'm NOT logging into, auto-mounts onto the desktop at login.  

But when I log into the SSD, the OS drive that I'm not logging into this time (the nvme) DOES NOT auto-mount at login.

But I'm not sure which factors  to look at, to see why the nvme correctly does NOT auto-mount?

What would account for the difference?

---

