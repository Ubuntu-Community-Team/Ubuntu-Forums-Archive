---
title: "Can't mount removable media: &quot;failed to execute child process exo-mount&quot;"
date: 2011-05-18
forum: Desktop Environments
---

### Post by pestie on 2011-05-18
I just upgraded Xubuntu from 10.04 LTS to 11.04 and I am no longer able to mount removable media from the "places" menu. The message I get:

"Failed to execute child process exo-mount (No such file or directory)"

I assume some wrapper process is attempting to execute a program called "exo-mount," but no such program exists anywhere in the repositories, according to a search with apt-file. The "exo-utils" package used to contain exo-mount, but the program no longer exists in that package.

Mounting from within Thunar works fine.

Any ideas?

---

### Post by Aaron_M on 2011-06-13
I am getting this error too. It seems to happen after not rebooting for a while.

---

### Post by Toz on 2011-06-13
What version of xubuntu are you using? 

Please note that exo-mount has been dropped from the exo-utils package for 11.04 ([https://launchpad.net/ubuntu/+source/exo/0.6.0-1](https://launchpad.net/ubuntu/+source/exo/0.6.0-1)). This will break other packages like xfce4-places-plugin that rely on exo-mount.

However, if you are using an earlier version of xubuntu, then there might be another reason. Usually this error message is the result of trying to unmount a volume that you still have an open connection to (ie. a Thunar window displaying the contents, a terminal window where the current directory is a directory on the mounted drive, etc). The solution here would be close all connected windows/apps and try again.

---

### Post by pestie on 2011-06-13
I'm using Xubuntu 11.04, and I had also discovered that exo-mount had been removed from the exo-utils package. It never ceases to amaze me that decisions like this get made. "Oh, yeah, here's a tool that performs a useful function in a simple, straightforward manner. Let's get rid of it. Yeah, it'll break a bunch of stuff that relies on it, but so what? There's a newer, better way to do what that tool used to do. It probably uses XML, 'cause XML is enterprise grade. What? You say people are unhappy? Who cares about people!? We're nerds, and we like shiny new things."

Meanwhile, over at Xubuntu World Headquarters: "Hey, the "places" function is broken." "Eh, screw it - it's only a highly-visible primary desktop function. They'll fix it eventually. Release Xubuntu 11.04!"

I love Xubuntu, and open source and free software in general - I really do - but I sure do get tired of this "change for change's sake" mentality that's taken firm hold over the last few years.

---

### Post by mike1312 on 2011-11-11
Same problem. But i cant mount it in thunar. So i did like in old times. I added my partitions to fstab. Here it is
```

proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=ccc8c0b5-2109-4ef7-9c59-59d299fc90d6 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda3 during installation
UUID=fe1b02e0-c4c3-40ca-a930-52f715a29de7 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/sdb1       /mnt/flash      auto    rw,user,noauto,exec,codepage=1251,iocharset=utf8        0       0
/dev/sda1       /mnt/c          auto    rw,user,noauto,exec,codepage=1251,iocharset=utf8        0       0

```Last two partitions is my flashdrive device and windows c: partition
I use russian cp1251 encoding to see proper russian filenames. So for your country it may be different
After inserting flash drive i just type ```
mount /mnt/flash
```

---

### Post by mike1312 on 2011-11-24
First ```
sudo aptitude show exo-utils
``` look at the version and remember it
Then ```
sudo aptitude remove exo-utils
``` and then answer no everywhere but the downgrading
Then ```
sudo aptitude forbid-version exo-utils=<the version>
```
And now you can safely upgrade

---

