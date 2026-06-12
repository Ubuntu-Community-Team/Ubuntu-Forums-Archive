---
title: "Booting fails at &quot;Checking Filesystems...&quot;"
date: 2006-09-18
forum: Desktop Environments
---

### Post by Boss Happy on 2006-09-18
There's a lot of history behind this so here goes...

I have a Dell PC 800 Mz, which I've upgraded from Breezy to Dapper.  I use Kubuntu.  I discovered that I didn't have HAL or ivman installed.  This appears to have been a bug with Kubuntu (but I've lost the link).

After installing HAL and ivman, I went about writing some udev scripts to automagically mount stuff.  I have a 250GB Maxtor external Firewire hard drive and I was trying to get to automount.
This is when things started getting weird.

After much fiddling, I decided it was time to reboot.  The shutdown process locked up, so a hard reboot was forced upon the box.  When the box was booting up, the screen flipped from the pretty scrolling messages to character based messages at "Checking filesystems..."  it appears the Superblock on my Maxtor was corrupted.  I ran fsck.ext3 on it but I kept getting something about "illegal seek"  which I assumed means, "You're trying to read from a drive that doesn't exist."

In frustration I ran:

```

mkfs -t ext3 /dev/sda5

```

This appears to have worked and after some more fiddling the box can boot up.  HOWEVER, I've created a udev script which maps the Maxtor harddrive to /dev/maxtor.  When I boot up the box the "Checking filesystem..." hangs and I get the "Corrupted Superblock" message.  I've learned that if I skip this step, the box will boot just fine, and I can mount/unmount the Maxtor drive without a problem.

I'm assuming this has to do with the sequence of boot time scripts.  My /etc/rcS.d director is as follows:
```

S01mountvirtfs
S01readahead
S02hostname.sh
S05keymap.sh
S07linux-restricted-modules-common
S08loopback
S10udev
S11mountdevsubfs
S15module-init-tools
S17procps.sh
S20checkroot.sh
S22mtab
S25mdadm-raid
S26lvm
S27evms
S30checkfs.sh
S35mountall.sh
S35quota
S39readahead-desktop
S40ifrename
S40networking
S40pcmcia
S41ipmasq
S42ipmasq-kmod
S45waitnfs.sh
S50hwclock.sh
S55dns-clean
S55pppd-dns
S55urandom
S60displayconfig-hwprobe.py
S70screen
S70x11-common
S70xorg-common
S80bootmisc.sh
S90console-screen.sh

```

Is there a problem with me changing when udev runs? Am I going about this in the right way?

Finally, where is the page on formatting posts?

Thanks.

---

