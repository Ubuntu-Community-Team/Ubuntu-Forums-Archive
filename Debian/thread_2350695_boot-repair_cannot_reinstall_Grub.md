---
title: "boot-repair cannot reinstall Grub"
date: 2017-01-26
forum: Debian
---

### Post by boot-me on 2017-01-26
[FONT=arial][SIZE=3]Hi all, long time reader, first time poster.

I'm having difficulty booting off of an encrypted LVM (no particular reason, just did the initial install that way) that had an issue with a backup. I am currently able to get to the data however, grub will not boot the OS, Debian. When I try to boot from the hard drive, I get a grub prompt showing "Minimal BASH like line editing is supported. For the first word,  TAB lists possible command completions. anywhere else TAB lists  possible device or file completions."

I initially started following directions from here and was using boot repair to try to reinstall grub: 

[https://itsfoss.com/fix-minimal-bash-line-editing-supported-grub-error-linux/](https://itsfoss.com/fix-minimal-bash-line-editing-supported-grub-error-linux/)

I'm currently booting off of USB with a boot-repair iso. When I run boot repair, I receive an error showing:
You may want to retry after decrypting your partitions. ([https://help.ubuntu.com/community/EncryptedPrivateDirectory](https://help.ubuntu.com/community/EncryptedPrivateDirectory))
Do you want to continue?
[/SIZE][/FONT][FONT=arial narrow][FONT=arial][SIZE=3]After confirming the drive is unencrypted, I am able to access the files with no issue from the file manager, I proceed and receive the following message:

Please close all your package managers (software center, update manager, synaptic, ...). Then try again.

Link below is a pastebin with the output from boot-info:
[http://paste.ubuntu.com/23871677/](http://paste.ubuntu.com/23871677/)

Any help would be appreciated, thanks![/SIZE][/FONT]
[/FONT]

---

### Post by oldfred on 2017-01-27
Moved to Debian sub-forum.

Do you have separate system partitions?
Boot-Repair is smart enough to ask & mount /boot, but does not mount other system partitions.
So you may have to do repairs the old fashioned way using a full chroot.
But have to separately mount /boot & other system partition(s) as well as /. 
Most instructions for chroot only have the mount of /.

 UEFI chroot (you would not need the ESP/efi system mount)
[http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380](http://askubuntu.com/questions/53578/can-i-install-in-uefi-mode-with-the-alternate-installer/57380#57380)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.
[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)
drs305 chroot to purge & reinstall grub2
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)
kansasnoob- full chroot one line version with &&---- change sda3 to your install
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)
[http://en.wikipedia.org/wiki/Chroot](http://en.wikipedia.org/wiki/Chroot)
Kernel panic at boot: not syncing. No init found - chroot to resolve
[http://ubuntuforums.org/showthread.php?t=2228437](http://ubuntuforums.org/showthread.php?t=2228437)

---

