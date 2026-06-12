---
title: "fdisk shows numerous /dev/loop"
date: 2019-09-16
forum: Desktop Environments
---

### Post by Geoff_Lane on 2019-09-16
Folks,

My machine is multiboot with Ubuntu, which is my main system along with Windows10 and Fedora.

There are no issues with operation but note I get a lot of loop devices showing if I run fdisk -l

The readout of loop is as follows;

```
Disk /dev/loop0: 3.7 MiB, 3825664 bytes, 7472 sectors
Disk /dev/loop1: 42.8 MiB, 44879872 bytes, 87656 sectors
Disk /dev/loop2: 149.9 MiB, 157184000 bytes, 307000 sectors
Disk /dev/loop3: 149.9 MiB, 157192192 bytes, 307016 sectors
Disk /dev/loop4: 3.7 MiB, 3825664 bytes, 7472 sectors
Disk /dev/loop5: 14.8 MiB, 15462400 bytes, 30200 sectors
Disk /dev/loop6: 14.8 MiB, 15462400 bytes, 30200 sectors
Disk /dev/loop7: 4.2 MiB, 4403200 bytes, 8600 sectors
Disk /dev/loop8: 956 KiB, 978944 bytes, 1912 sectors
Disk /dev/loop9: 80.2 MiB, 84094976 bytes, 164248 sectors
Disk /dev/loop10: 140.7 MiB, 147501056 bytes, 288088 sectors
Disk /dev/loop11: 140.7 MiB, 147501056 bytes, 288088 sectors
Disk /dev/loop12: 94.8 MiB, 99368960 bytes, 194080 sectors
Disk /dev/loop13: 54.4 MiB, 57065472 bytes, 111456 sectors
Disk /dev/loop14: 80.2 MiB, 84094976 bytes, 164248 sectors
Disk /dev/loop15: 89 MiB, 93327360 bytes, 182280 sectors
Disk /dev/loop16: 94.7 MiB, 99250176 bytes, 193848 sectors
Disk /dev/loop17: 35.3 MiB, 37027840 bytes, 72320 sectors
Disk /dev/loop18: 4 MiB, 4218880 bytes, 8240 sectors
Disk /dev/loop19: 132 KiB, 135168 bytes, 264 sectors
Disk /dev/loop20: 132 KiB, 135168 bytes, 264 sectors
Disk /dev/loop21: 1008 KiB, 1032192 bytes, 2016 sectors
Disk /dev/loop22: 54.4 MiB, 57069568 bytes, 111464 sectors
Disk /dev/loop23: 88.7 MiB, 92983296 bytes, 181608 sectors
```

This seems to amount to over 1.25GB so am wondering what they are and are they a problem?

I do have VirtualBox on my Windows partition and I understand they are associated with virtual partitions but I only have one virtual partition, not 24

Geoff

---

### Post by cruzer001 on 2019-09-16
Snap packages create a dev/loop when installed.  I think you got a bunch

---

### Post by oldfred on 2019-09-16
I remove all snaps and install standard repository files. But they are now converting some apps to just being snaps. 
You can list without snaps.
       exclude snaps in commands
lsblk -af |grep -sv loop
df | egrep -v /dev/loop
lsblk -e7 -f
df -h -x squashfs 
    

Snaps used to be really slow in loading. They have made improvements, so not as bad as when this was posted.
       boot time cut in half by removing snap
[https://ubuntuforums.org/showthread.php?t=2391341](https://ubuntuforums.org/showthread.php?t=2391341)
[https://ubuntuforums.org/showthread.php?t=2409173](https://ubuntuforums.org/showthread.php?t=2409173)
[https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements](https://blog.ubuntu.com/2019/03/28/snap-startup-time-improvements)
General snap discussion:
[https://ubuntuforums.org/showthread.php?t=2411218](https://ubuntuforums.org/showthread.php?t=2411218)
[https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb](https://askubuntu.com/questions/1039411/how-can-i-replace-snap-application-such-as-gnome-calculator-with-a-deb) & 
[https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead](https://askubuntu.com/questions/948861/why-would-i-want-to-install-a-snap-if-i-can-install-via-apt-instead)

---

### Post by deadflowr on 2019-09-16
To add look at what snaps are installed and 
see how many revisions they have with
```
snap list  << shows installed snaps
snap list --all  << shows all snaps and all revisions
```
There are several simple methods to clear them out
Easiest being this a simple script found here:
[https://askubuntu.com/a/1040131]("https://askubuntu.com/a/1040131")

Another thing to do is you can try setting the number of revisions to keep to a lower number
by using the snap commands found here for refresh.retain.
[https://snapcraft.io/docs/system-options]("https://snapcraft.io/docs/system-options")
I set mine to the most minimal, 2
like
```
sudo snap set system refresh.retain=2
```

But for what's it's worth 1.25GB for that many isn't actually that bad.
Being the snap packages contain all necessary software within there loop mounts to run.

---

### Post by TheFu on 2019-09-16
A handy alias for df:
```
alias dft='df -hT -x squashfs -x tmpfs -x devtmpfs'
```

I don't know if it hides loop devices, since I don't use snaps at all, anywhere.  It does remove pseudo-file systems that don't use any storage, however.  Snaps use storage, but that is counted in the real storage numbers, so all the loop devices can be safely ignored.

---

### Post by Geoff_Lane on 2019-09-18
> **oldfred said:**
> I remove all snaps and install standard repository files. But they are now converting some apps to just being snaps. 
You can list without snaps.
       exclude snaps in commands
lsblk -af |grep -sv loop
df | egrep -v /dev/loop
lsblk -e7 -f
df -h -x squashfs 
    


Why do they do this, is this an Ubuntu thing or Debian?

Those commands are useful, thank you.

Geoff

---

### Post by TheFu on 2019-09-18
> **Geoff_Lane said:**
> Why do they do this, is this an Ubuntu thing or Debian?

snaps solve some problems while creating others.  It is a trade off decision.  There are many places with discussions of the pros/cons for snaps, flatpaks, appimages. These are roughly the same.  Linux always brings choices. ;)

Using loop devices has been normal for over 20 yrs, just not normally to the levels seen with snaps. Previously, it was an admin who used them most commonly for access to image backups.

What most people need to know is that snaps aren't going away.  19.10 will be greatly expanding the use of snaps and there will be issues and broken workflows. More RAM will be used. More storage will be used. Some packages will not be available in any other way except via a snap, according to the snap team.  Some things will work better with snaps and they should provide significantly more protection against malware and viruses.
The main reason for snaps is to make developer packaging more universal - except we get 3 versions of almost the same things between snaps, flatpaks and appimages.  For end-users, like us, it means the same issues we always had around packing for a different OS, so we have to have all 3 of the options.

---

