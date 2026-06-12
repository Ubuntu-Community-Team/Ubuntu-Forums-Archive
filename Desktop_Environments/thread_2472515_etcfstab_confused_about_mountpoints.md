---
title: "/etc/fstab confused about mountpoints?"
date: 2022-03-01
forum: Desktop Environments
---

### Post by alexloz on 2022-03-01
This is in Ubuntu 20.04 - I don't think it existed in the old version.

I've known that systemctl seems to want to own the mounting of any device in /etc/fstab, such that if I try to mount a nonstandard device to a known mountpoint, I need to have it reload its values, or it will unmount it pretty quickly.

What's new is that I'm seeing this behavior even for known mountpoints - in kind of an unpredictable fashion. I think that it has to do with the fact that I'm mounting from /dev/md/?? instead of /dev/md?? , but I couldn't swear that's the problem.

Any help in fixing or troubleshooting this would be appreciated!

---

### Post by TheFu on 2022-03-01
I don't have RAID on 20.04, but on my 20.04 systems, I haven't been surprised too much with systemd.mount, unless I was trying to use systemd-extended mount options like x-systemd.automount.  That sent me running back to autofs.

If you post _more facts_, like exact **fstab** lines, exact file systems, some **df -Th** output and the output from a sudo mdadm --detail /dev/md? command, perhaps someone could help?

I don't think /dev/md/1 is any different than /dev/md1.  Use whatever is more convenient. The /dev/md/1 appears to be a symlink to ../md1 here.  You could use LABEL= for the mount, if you like:
```
/dev/disk/by-label$ ls -l
lrwxrwxrwx 1 root root   9 Mar  1 01:45 R2-Array -> ../../md2
lrwxrwxrwx 1 root root   9 Mar  1 01:45 RAID1-Array -> ../../md1
```

That would be:
```
LABEL=RAID1-Array    /raid      ext4 noatime  0 2
LABEL=R2-Array    /Data/r2      ext4 noatime   0        2
```
on my system.  BTW, this is EXACTLY the way I mount those arrays. I prefer using LABEL= to mount things. Much easier for us dumb humans.  If I was using LVM, I'd use /dev/<vgname>/<lvname> in the fstab mount.  

This assumes the disks aren't USB connected. For USB connected stuff, I use autofs, always. USB connections just aren't stable enough to use hard-mounts. I've been burned.

---

### Post by DuckHook on 2022-03-01
> **TheFu said:**
> …For USB connected stuff, I use autofs, always. USB connections just aren't stable enough to use hard-mounts. I've been burned.
I agree that USB connections are far too fragile for hard-mounts. But why even autofs? I use usbmount. I've found that with usbmount, udev doesn't go crazy when the USB drive unexpectedly disconnects.

---

### Post by TheFu on 2022-03-01
[LIST]
[*]Reason 1: Never heard of it. Doesn't seem to be in the system repos
```
$ usbmount
usbmount: command not found
```
Normally, there would be a package to install listed with the command right?
[*]Reason 2: I'm old and have been using automountd and autofs for 25+ yrs. Nothing new to learn. autofs is in a package in the standard repos.  I did look at systemd-automount and found it would never release the mounts, which was unacceptable for my use.
[*]Reason 3: ANYTHING that mounts _without my explicit control_ over the location (never /media!) and mount options is a failure in my book. The power to mount is the power to destroy.  There are some nasty malware which can be deployed just by inserting a USB device into a computer, including Linux. No way do I want some random flash drive to get any notice when plugged in.  Now, if I've configured the flash drive for use, via autofs, then I just need to access to location where it should be mounted (I use /misc/<LABEL> typically) and control the options as needed for the partitions.
[/LIST]

Linux File System Hierarchy Standards document [https://refspecs.linuxfoundation.org/FHS_3.0/fhs/ch03s11.html](https://refspecs.linuxfoundation.org/FHS_3.0/fhs/ch03s11.html)  The entire automatic mount of random storage devices really concerns me.

I got nuthin' else - except ignorance.

---

### Post by DuckHook on 2022-03-02
> **TheFu said:**
> 
Reason 1: Never heard of it. Doesn't seem to be in the system repos
```
$ usbmount
usbmount: command not found
```
Normally, there would be a package to install listed with the command right?
:confused:
That's odd. Here's the result of my query:
```
duckhook@Zeus:~$  apt show usbmount
Package: usbmount
Version: 0.0.22
Priority: extra
Section: universe/admin
Origin: Ubuntu
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Rogério Brito <rbrito@ime.usp.br>
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Installed-Size: 82.9 kB
Depends: lockfile-progs, udev, util-linux (>> 2.16)
Recommends: pmount
Homepage: http://usbmount.alioth.debian.org/
Download-Size: 15.1 kB
APT-Sources: http://ca.archive.ubuntu.com/ubuntu impish/universe amd64 Packages
Description: automatically mount and unmount USB mass storage devices
 This package automatically mounts USB mass storage devices (typically
 USB pens) when they are plugged in, and unmounts them when they are
 removed. The mountpoints (/media/usb[0-7] by default), filesystem types
 to consider, and mount options are configurable. When multiple devices
 are plugged in, the first available mountpoint is automatically
 selected. If the device provides a model name, a symbolic link
 /var/run/usbmount/MODELNAME pointing to the mountpoint is automatically
 created.
 .
 The script that does the mounting is called by the udev daemon.
 Therefore, USBmount requires a 2.6 (or newer) Linux kernel.
 .
 Firewire devices are also supported by USBmount.
 .
 USBmount is intended as a lightweight solution which is independent of
 a desktop environment. Users which would like an icon to appear when an
 USB device is plugged in should use the pmount and hal packages
 instead.
```
> Reason 2: I'm old and have been using automountd and autofs for 25+ yrs. Nothing new to learn. autofs is in a package in the standard repos.  I did look at systemd-automount and found it would never release the mounts, which was unacceptable for my use.
:KS
Age is always a legitimate excuse in my books.
> Reason 3: ANYTHING that mounts _without my explicit control_ over the location (never /media!) and mount options is a failure in my book. The power to mount is the power to destroy.  There are some nasty malware which can be deployed just by inserting a USB device into a computer, including Linux. No way do I want some random flash drive to get any notice when plugged in.  Now, if I've configured the flash drive for use, via autofs, then I just need to access to location where it should be mounted (I use /misc/<LABEL> typically) and control the options as needed for the partitions.

This is a very legitimate concern. I swear I learn something new from you every time you post. FWIW, I've been using usbmount since, ohh, Precise? Maybe even before that. I'm not sure that automounting=autorun, but you make a good point. It's just that I was burned by hard mounts too and found this solution via web searches. I've inadvertently unplugged USB drives while file transfers were still taking place, but with usbmount, although the file still got corrupted, the kernel didn't go nuts, which was a far better experience than what happened with hard mounts.

However, I will reconsider the practice in light of your advice.
> I got nuthin' else - except ignorance.
Hardly!

---

### Post by alexloz on 2022-03-02
Ok, hopefully this explains what I'm talking about. The cd into the directory causes it not to be unmounted because it's in use.

```
# df | grep dvd1
# grep dvd1 /etc/fstab
/dev/md/myhost:dvd1     /stuff/dvd1    ext4     auto,nofail,x-systemd.device-timeout=10ms     0       0
# ls -l /dev/md/myhost\:dvd1
lrwxrwxrwx 1 root root 10 Mar  2 16:18 /dev/md/myhost:dvd1 -> /dev/md116
# mount /stuff/dvd1
# df | grep dvd1
# mount /stuff/dvd1;cd /stuff/dvd1
# df | grep dvd1
/dev/md116      576221760  573008260          0 100% /stuff/dvd1
```

---

### Post by DuckHook on 2022-03-02
You have confused me:

Are you trying to hard mount a DVD drive?

If so, then TheFu's and my earlier posts are very much on topic. It is a bad idea to mount removable media in fstab.

You should either be using TheFu's suggestion of autofs, my option of usbmount, or just mounting manually every time you want access to the drive.

If dvd1 is not, in fact, a DVD drive, then your choice of using "dvd1" for the mountpoint is very confusing and you need to provide more information about what exact physical media you are trying to mount.

---

### Post by alexloz on 2022-03-02
No, it's a raid partition that's called "dvd1". It's a simple raid array, which contains dvd images. The problem is that I am trying to mount it manually but something is unmounting it if I don't cd into the directory immediately. This only happens for mountpoints which are in /etc/fstab, I can mount it anywhere else with no trouble.

```
md116 : active raid6 sdq3[0] sdj3[5] sdi3[2] sdf3[6] sdb3[7]
      585541632 blocks super 1.2 level 6, 512k chunk, algorithm 2 [5/5] [UUUUU]
      bitmap: 0/2 pages [0KB], 65536KB chunk
```

---

### Post by DuckHook on 2022-03-02
I should further note that /dev/md implies a RAID array. If your device is, in fact, a DVD drive, then what is it doing in a RAID array?

EDIT:

Sorry. Posted before seeing your latest.

---

### Post by alexloz on 2022-03-02
Another example : 
```

# df | grep dvd3
# grep dvd3 /etc/fstab
/dev/md/myhost:dvd3     /stuff/dvd3                         ext4                  auto,nofail,x-systemd.device-timeout=10ms     0       0
# ls -l /dev/md/myhost\:dvd3
lrwxrwxrwx 1 root root 9 Mar  2 16:18 /dev/md/myhost:dvd3 -> /dev/md83
# mkdir /tmp/mnt
# mount /dev/md83 /tmp/mnt
# df | grep mnt
/dev/md83       384103492  362911596    1657460 100% /tmp/mnt
# umount /tmp/mnt
# mount /stuff/dvd3
# df | grep dvd3
# mount /stuff/dvd3 ; cd dvd3
# df | grep dvd3
/dev/md83       384103492  362911596    1657460 100% /stuff/dvd3
```

---

### Post by DuckHook on 2022-03-02
> **alexloz said:**
> No, it's a raid partition that's called "dvd1". It's a simple raid array, which contains dvd images. The problem is that I am trying to mount it manually but something is unmounting it if I don't cd into the directory immediately. This only happens for mountpoints which are in /etc/fstab, I can mount it anywhere else with no trouble.
Ah. Okay.

What do your logs tell you? Filter for file system, mounts and errors.

---

### Post by TheFu on 2022-03-02
I've never used a storage device mout with ':' in the name. 

Try quoting it .... or just use /dev/md116 or a LABEL or UUID instead.
```
"/dev/md/myhost:dvd1"     /stuff/dvd1    ext4     auto,x-systemd.device-timeout=10ms     0       0
```

That seems like a really short timeout. A disk takes longer than that to spin up, doesn't it?  
```
"/dev/md/myhost:dvd1"     /stuff/dvd1    ext4     nofail,errors=remount-ro     0       2
```

I know that systemd will create non-existent directories for mount points, but better to be sure.
```
sudo mkdir -p   /stuff/dvd1   
```
I like the name, /stuff. That's where I put junk that will never be backed up - files for temporary needs or travel entertainment on a laptop.

After making the change, let systemd know ... shouldn't be necessary, but ... 
```
sudo systemctl daemon-reload
```
then mount it:
```
sudo mount -a
```

---

### Post by DuckHook on 2022-03-02
> **TheFu said:**
> I've never used a storage device mout with ':' in the name.
You beat me to this by a few seconds.

---

### Post by TheFu on 2022-03-02
> **DuckHook said:**
> You beat me to this by a few seconds.

If using PCI channels for the mount, there are ':' in the path, but that's more of any enterprise storage thing.

To see all the options, just use:
```
$ find /dev/disk/ -type l
```
Looks like the whole slot-channel-disk-slice thing is available. I suppose if you have 300 disks connected over FC, that would be a cleaner method to keep things straight.

I've never figured out how to have df/mount output the names I used for the mount. Even for LVM, when I use /dev/<vgname>/<lvname> to mount, the output for df and mount always show /dev/mapper/ junk.

---

### Post by alexloz on 2022-03-02
I've tried what I think were all the suggestions. I also did something that I do know works. 

I think something is getting lost in my explanation - it IS getting mounted, but then it gets immediately unmounted (unless I cd into it) if it doesn't match the device name listed for that mountpoint in /etc/fstab. I can't reliably reproduce this issue; sometimes it works, and it seems to work if I create symlinks and use them in /etc/fstab, or if I mount the wrong devices to certain other mountpoints. 

```
# grep dvd4 /etc/fstab
"/dev/md/myhost:dvd4"   /stuff/dvd4                         ext4                  auto,nofail   0       0
# mount /stuff/dvd4
# df | grep dvd4
# ls -l /dev/md/myhost\:dvd4
lrwxrwxrwx 1 root root 10 Mar  2 16:18 /dev/md/myhost:dvd4 -> /dev/md106
# emacs /etc/fstab
# grep dvd4 /etc/fstab
/dev/md106      /stuff/dvd4                         ext4                  auto,nofail   0       0
# mount /stuff/dvd4
# df | grep dvd4
/dev/md106      576224832  499701068   47230148  92% /stuff/dvd4

```
The md: names are (as I understand it) the preferred way to deal with raid arrays as of superblock 1.2 (or possibly earlier). This is because mdadm likes to assign its own device names freely and it avoids having to deal with mdadm.conf (which is how I used to do things). This all worked on an earlier version of Ubuntu.
The md devices are automatically generated from the information in the superblock:

```
# mdadm --examine /dev/sdj5
/dev/sdj5:
          Magic : a92b4efc
        Version : 1.2
    Feature Map : 0x1
     Array UUID : 0c398728:cb9ecae9:880fd3cc:1b8ae268
           Name : myhost:dvd4  (local to host myhost)
  Creation Time : Tue Jan 24 02:53:14 2017
     Raid Level : raid5
   Raid Devices : 4

```

---

### Post by alexloz on 2022-03-02
> [QUOTE][COLOR=#000000][INDENT]What do your logs tell you? Filter for file system, mounts and errors.[/INDENT]
[/COLOR][INDENT]
[/INDENT]
[/QUOTE]

I'm not sure which logs I should be looking at, the ones I know about (dmesg is the only one I can think of) don't seem to show anything.

---

### Post by DuckHook on 2022-03-02
[https://www.howtogeek.com/499623/how-to-use-journalctl-to-read-linux-system-logs/](https://www.howtogeek.com/499623/how-to-use-journalctl-to-read-linux-system-logs/)

The new (well, not so new anymore) journalctl can give you additional data. syslog and kern.log are also useful, but require you to filter for relevant entries. Otherwise, you get overwhelmed with fluff.

It's not really possible to give you a primer on log reading in a forum post. It's a bit of a black art, but generally involves grepping for key words and phrases. It's also very important to note exact and specific times when your mount fails and then look at the journal entries for that exact time.

---

### Post by alexloz on 2022-03-02
Thanks! I have experience looking at logfiles, but somehow it never occurred to me something for this would be in system.log.

```
Mar  2 20:36:24 myhost kernel: [22512.432175] EXT4-fs (md84): mounted filesystem with ordered data mode. Opts: (null). Quota mode: none.
Mar  2 20:36:24 myhost systemd[1]: stuff-dvd5.mount: Unit is bound to inactive unit dev-md-myhost:dvd5.device. Stopping, too.
Mar  2 20:36:24 myhost systemd[1]: Unmounting /stuff/dvd5...
Mar  2 20:36:24 myhost systemd[11438]: stuff-dvd5.mount: Succeeded.
Mar  2 20:36:25 myhost systemd[1]: stuff-dvd5.mount: Succeeded.
Mar  2 20:36:25 myhost systemd[1]: Unmounted /stuff/dvd5.

```

Something very similar comes out of journalctl if I grep for dvd5.
Where to next? It doesn't seem to indicate why it's unmounting it; I'm not sure what the "inactive unit" stuff means either. I googled "systemd log" but it was hinted that journalctl would show me that.

For a volume that did mount correctly, there's an addition of :
```
Mar  2 20:19:04 myhost umount[26960]: umount: /stuff/media8: target is busy.

```
but I can't guess as to why it thinks it was in use.

and from our example above, replacing the linked device in etc/fstab with the actual device name, we get:
```

Mar  2 20:46:47 myhost systemd[11438]: stuff-dvd4.mount: Succeeded.
Mar  2 20:46:47 myhost systemd[1]: stuff-dvd4.mount: Succeeded.
Mar  2 20:46:49 myhost kernel: [23137.069190] EXT4-fs (md106): mounted filesystem with ordered data mode. Opts: (null). Quota mode: none.

```

---

### Post by DuckHook on 2022-03-02
Web searches found these:

[https://www.claudiokuenzler.com/blog/1124/linux-mount-not-working-systemd-unit-is-bound-to-inactive](https://www.claudiokuenzler.com/blog/1124/linux-mount-not-working-systemd-unit-is-bound-to-inactive)
[https://github.com/systemd/systemd/issues/1741](https://github.com/systemd/systemd/issues/1741)

and perhaps most useful to you:

[https://dba-tips.blogspot.com/2020/12/systemd-unit-awscsrdbmount-is-bound-to.html](https://dba-tips.blogspot.com/2020/12/systemd-unit-awscsrdbmount-is-bound-to.html)

TL;DR

It seems that systemd will sometimes get confused by a mountpoint that is changed in fstab while the system is active. The last link proposes a solution wherein the mountpoint gets refreshed by deleting then re-creating. I have never had anything like this happen to me, so can only point you along a road trod by others.

---

### Post by alexloz on 2022-03-02
Thanks - I actually knew about most of those issues from Ubuntu 15, which I did have to deal with, updating systemctl etc. In my case, fstab and all mountpoints are not being changed. Nothing in those posts seems to fix this issue - maybe there's someone with more experience regarding how and why systemd does what it does?
_or_ if there's a way to just stop it from controlling mountpoints, that would work.

---

### Post by TheFu on 2022-03-03
stuff-dvd5.mount is a systemd unit file.
We can "start" and "stop" them just like any other service in a systemd unit file ... "networking".
It is automatically generated by systemd when the fstab is modified, in theory and placed into the systemd-controlled part of the file system, somewhere.  I don't recall if that is /lib/ or /var/ ... you can look for *mount files to find them.

By using **autofs**, I avoid all the systemd control over mounts, except those for the core parts of the OS. Could that work for you? I wouldn't use autofs for RAID storage, but it will work.

And let's be very clear. Nobody here works for Canonical. We are volunteers sharing experience. Nothing more. We don't have any way to contact Canonical officially.  If you want to attempt that, they used to be active on IRC, but that format requires pithy questions.  1-2 yrs ago, there was some uproar about IRC and the owning company changing which had about 90% of the users leave it. When Canonical moved their IRC support, I didn't follow them.

---

### Post by alexloz on 2022-03-04
Hi - I wanted to update that upon further googling I may have found a solution. Running:
```

systemctl mask devname.mount

```
seems to allow the device to be mounted.

---

### Post by DuckHook on 2022-03-04
Thanks for following up with your solution!

---

### Post by TheFu on 2022-03-05
Masking will certainly prevent it from happening.  "devname" is tied to the mount location. It is not literal. It needs to be replaced with the correct filename.

Happy that you found a solution that works.

---

