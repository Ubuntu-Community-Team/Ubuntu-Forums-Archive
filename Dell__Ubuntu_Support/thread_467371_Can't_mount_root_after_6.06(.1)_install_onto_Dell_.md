---
title: "Can't mount root after 6.06(.1?) install onto Dell 2950 (PERC 5/i RAID controller)"
date: 2007-06-07
forum: Dell  Ubuntu Support
---

### Post by beowabbit on 2007-06-07
(Yes, I have searched the forums and seen other people's issues with this hardware -- the fix I found didn't work for me.)

I'm trying to install Ubuntu 6.06 LTS onto a Dell 2950, with a PERC 5/i RAID controller and two dual-core Xeon processors.

I found [this thread]("http://ubuntuforums.org/showthread.php?t=226114") which suggests that it should be possible, if I modify the initramfs after the install but before rebooting.  So I tried following the instructions given there (as root, i.e. after "sudo -s" in a terminal window):
> mount /dev/sdb2 /target
chroot /target
echo "megaraid_sas" >> /etc/mkinitramfs/modules
mkinitramfs -o /boot/initrd.img-2.6.15-23-386 2.6.15-23-386
(That's all transcribed by hand, so I might have mistyped something.)  The instructions at the linked thread specify a different kernel, but I based my mkinitramfs command on what's already in /boot.  (I am trying to use the x86 install CD, partly because I've seen reports of trouble with the x86-64 version and partly for compatibility with our other machines.)

However, after that change, I am still unable to boot the installed system.  The graphical boot screen shows "Mounting root file system..." and then after a pause "Waiting for root file system..." and hangs there; if I CTRL-ALT-F1 to tty1, I see "Uncompressing Linux... OK, booting the kernel." and then after a *long* pause, "ALERT!!! /dev/sdb2 does not exist, dropping to a shell!!!" and I end up in a busybox shell (presumably compiled into the kernel).  Unfortunately it has no dmesg command, although I also think at this point there's no kernel output other than what's on the screen.

(That's the same behaviour I had before tweaking the initramfs as suggested in the linked thread.)

Interestingly, I see in that thread that the installer doesn't detect the onboard Ethernet cards.  That's not the case for me.  Also, in other threads, I see that there should be several sd* devices for the individual drives, as well as an sd for just the virtual drive provided by the RAID controller; that doesn't appear to be the case for me (at least when booted from the live-CD).

Can anybody point me at additional suggestions for getting Ubuntu booting on this hardware?

(Also, since we have 8Gb of RAM in this machine I presume I'll need to replace the kernel once it's booting to see all the RAM.  If there are any tips I should know about about that in advance, please let me know, given that it seems to take some work to get a kernel+initrd combo on the machine that sees the RAID controller in the first place.)

---

### Post by lavajumper on 2007-09-24
I noticed this thread was unanswered, so.....

I had a similar problem on our 2950. It turned out 6.06 installation didn't write the grub menu quite right. I had to use hd(5,0) on our 5 disk raids, and hd(3,0) on our 3 disk.  (so the number of real disks +1, starting at 0)

In order to boot, hit the 'esc' key, choose a kernel, and choose 'e' for edit the entry. After you get the machine up, edit /boot/grub/menu.lst to reflect the correct disk. 

Also, any time a kernel update comes through, I have to go back and edit the /boot/grub/menu.lst. My guess is that at some point this will get fixed, I'll edit the grub menu and won't be able to boot (which means a drive in the middle of the night <grrr>), but such is life in ServerLand.

I hope this helps, even if it is a little late.

---

