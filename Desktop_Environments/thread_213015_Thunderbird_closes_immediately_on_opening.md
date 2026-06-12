---
title: "Thunderbird closes immediately on opening"
date: 2006-07-10
forum: Desktop Environments
---

### Post by SquareBoy on 2006-07-10
Hello, I've tried searching these forums but haven't had any luck. My problem is that whenever I start Thunderbird it opens a window, then closes it about 0.5 seconds later.

Things that might be relevant
- It has worked before ie I've been able to look through my old mails from that profile.
- Since then I have added windows fonts and edited fstab to mount my fat32 partitions automatically. I can't think of anything else. (I've only installed Ubuntu in the last couple of days)
- The profile I'm trying to use is on a shared fat32 drive
- I have tried using the package manager to remove and re-install Thunderbird but it hasn't helped. (I suspect that it didn't actually re-download the package)
- Firefox is working fine with it's profile on the same drive
- My fstab now looks like (my profiles are on /dev/sda5):

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda5       /media/stuff    vfat    users,rw,umask=000 0       1
/dev/sda1       /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
/dev/sda4       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc1       /media/portable vfat    users,rw,umask=000     0       0
```

Any help would be greatly appreciated, thanks.

---

### Post by SquareBoy on 2006-07-13
Ok, for anyone that finds this in a search this was solved by the latest round of updates.

I didn't notice if Firebird was updated but some fonts definitely were, so it seems likely that the instructions I followed to add windows fonts did something that Firebird or Ubuntu didn't like.

---

### Post by dogscoff on 2007-08-22
I know this is an old thread, but I came across it recently when I experienced a similar problem on my wife's dell/feisty machine, and I had some extra information to contribute to a problem that obviously can still occur. just like the OP described, Thunderbird would close immediately after opening.

In my case, the problem was definitely caused by an attempt to install MS fonts. (Not via the MSfonts pack in the repository, which doesn't include all the fonts found in Wondows, but through some wyrd magic involving copying the ttf files and then rebuilding the font cache). Unfortunately, I couldn't fix this problem with a "round of updates" like the OP because my machine was already fully updated! 

Therefore I tried uninstalling/ reinstalling Thunderbird through the software library. Like the OP, it didn't re-download the package- I suspect it was just pulling the old install out of the recycle bin. Bad Linux, lazy Linux! ;)

However, uninstalling Thunderbird, then rebooting the machine, and *then* re-installing it seemed to do the trick. It actually went online and downloaded the software anew, and from then on it worked fine. Restoring all my email was a bit of a drag, but it fixed it in the end. 

I hope this helps anyone else who encounters the same trouble.

---

