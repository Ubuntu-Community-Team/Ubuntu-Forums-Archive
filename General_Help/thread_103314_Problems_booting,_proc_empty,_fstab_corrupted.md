---
title: "Problems booting, /proc empty, fstab corrupted"
date: 2005-12-13
forum: General Help
---

### Post by tirian on 2005-12-13
Hello,

I'm having some problems with my system. When I try to boot, the system logger fails to start. Then it switches to the first virtual console, displays a ton of error messages and hangs. I've checked dmesg and /var/log/messages and there is nothing strange that I can see. I think something is panicing as well.

However, if I boot into safe mode, I can get a little farther. I can log in, but my /proc is totally empty. In addition if I try to do an ls in /etc, it displays: "ls: fstab: Input/ouput error" and "ls: kernel-img.conf: Input/output error".

I've tried to check the disk with fsck on /dev/hda5 and /dev/hda7 (my root and /home partitions) from the ubuntu live CD but the check comes up clean.

Something that may have caused this problem: I was surfing the web on my wireless and my X locked up. I could still use my mouse, but I coun't interact with any of the windows nor enter any keyboard input. So, I killed X using ctl+alt+bkspace, but then my system locked up. I performed a hard reboot and now problems abound.

Can anyone help?

I know I can "just reinstall", but I'd like to know how to fix this.

~Tirian

---

### Post by JimmyBEng on 2005-12-14
consider this thread.
[http://www.ubuntuforums.org/showthread.php?t=86589](http://www.ubuntuforums.org/showthread.php?t=86589)
I was having a problem similar to yours and to the guy and this thread.
So maybe force the fsck.

---

