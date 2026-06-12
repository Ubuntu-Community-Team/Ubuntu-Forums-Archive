---
title: "Kernel panic"
date: 2005-09-11
forum: Desktop Environments
---

### Post by topic58 on 2005-09-11
Hi, using Ubuntu 5.04 on a desktop. After update to new kernel 2.6.10-5-386, my pc will not start after reboot. It says kernel panic and the name on the new kernel 2.6.10-5-386. No way I can get it going. Also a friend of mine have this problem. What to do here? Anyone with a suggestion? Tried everything to get it going I know of. I can add that I also have some unofficial updates and apps from apt-get.

---

### Post by Markpy on 2005-09-11
In order to get you Ubuntu installation working again you will need a bootable Linux distro, either installed on your hard disk/local network or a LiveCD.

BTW, I haven't tested this procedure...

1) Boot the rescue Linux distro.
2) Mount the Ubuntu root partition.
**Terminal:** (replace the [color=Red]**red**[color=Black] if appropriate[/color][/color])
```

# mkdir /tmp/ubuntu
# mount **[color=Red]/dev/hda1[/color]**[color=Red][color=Black] /tmp/ubuntu -t [color=Red]**ext3**[/color][/color][/color]

```
3) Mount the rescue Linux's proc onto the Ubuntu root partition.
**Terminal:**
```

# mount -t proc none /tmp/ubuntu/proc

```
4) Chroot into the Ubuntu environment and set environmental variables.
**Terminal:**
```

# chroot /tmp/ubuntu /bin/bash
# source /etc/profile

```
5) Remove the broken kernel package.
**Terminal:**
```

# dpkg -r linux-image-2.6.10-5-386

```
6) Build/install a working kernel image.
To build a kernel you should refer to [HOWTO: Kernel Compilation.]("http://ubuntuforums.org/showthread.php?t=43065")
To install a different kernel just get one off apt.
**Terminal:**
```

# apt-get install linux-image-2.6.11-1-386

```
7) Reboot.
[b]Terminal:
[/b]```

# reboot

```

I hope that helps :)

P.S. For a safety measure you should always have 2 working kernels available on you boot loader so that when you upgrade/rebuild one you know that the other will be fine.

---

