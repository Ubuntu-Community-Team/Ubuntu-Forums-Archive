---
title: "Update Dell PPA Entry"
date: 2008-09-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Denny Johnson on 2008-09-06
1420n 7.04, recently upgraded to 7.10, then 8.04.
All seems to be OK ex a couple of resume from suspend issues:
- no backlight
- no wireless, "networking disabled"

Updating Dell's PPA Entry is a known issue
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04)
[http://linux.dell.com/wiki/index.php/Ubuntu_8.04](http://linux.dell.com/wiki/index.php/Ubuntu_8.04)

The Fix: In /etc/apt/sources.list. Change PPA entry from 

```
deb http://ppa.launchpad.net/dell-team/ubuntu gutsy main
deb-src http://ppa.launchpad.net/dell-team/ubuntu gutsy main

```
to

```
deb http://ppa.launchpad.net/dell-team/ubuntu hardy main
deb-src http://ppa.launchpad.net/dell-team/ubuntu hardy main
```

Finally, update packages:

```
$ sudo apt-get update
$ sudo apt-get upgrade
```

But, nothing re ppa or launchpad or dell in my /etc/apt/sources.list
```
# 
# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
```

Can I just add the Hardy code from the fix?
Any suggestions appreciated
Thanks

---

### Post by anjilslaire on 2008-09-06
It should have been updated. Be sure to use sudo to make the changes.

---

### Post by Denny Johnson on 2008-09-07
I added the Hardy code, updated and upgraded.
No improvement til I followed w the recommendations of a couple of other posts:
Strixy said: “When you upgrade your dist. you also have to go in and manually change your Dell specific repositories in Synaptic to reflect the change. That will get you the right kernel version with a working wireless stack.”
 "Actually, the kernel is 2.6.24-19 generic and you must install the linux-backports-modules-2.6.24-19 generic using Synaptic to have the Wireless LED runing (and linux-backports-modules-hardy, linux-backports-modules-hardy-generic as well)." [Thanks arverne]

I am now able to run 2.6.24-19 generic, have wireless and backlight at boot and at resume from suspend.
Only issue I'm seeing now is no sound. 
Is there a sound related package that needs to be installed in Synaptic???
Suggestions?????

---

### Post by anjilslaire on 2008-09-07
here we go:
Ubuntu 8.04/Issues/No Sound After Distribution Or Kernel Upgrade

[http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04/Issues/No_Sound_After_Distribution_Or_Kernel_Upgrade")

> 
If already running Ubuntu 8.04 and upgrading to kernel 2.6.24-17-generic

Restore name of sound driver that old modem driver renamed:

$ cd /lib/modules/2.6.24-17-generic/ubuntu/sound/alsa-driver/pci/hda
$ sudo mv snd-hda-intel.ko.REPLACEDBYhsfmodem snd-hda-intel.ko

Remove old sound drivers from kernel module directory:

$ cd /lib/modules/2.6.24-17-generic/updates
$ sudo rm snd-hda-intel.ko
$ sudo rm snd-hda-codec.ko

Rebuild initrd and reboot:

$ sudo depmod -a
$ sudo update-initramfs -u
$ sudo reboot



Also, check the sound mixer channels and ensure they're all turned up. I've seen an odd channel turned down that muted the audio before.

---

### Post by Denny Johnson on 2008-09-07
Thanks again,
I tried that just before I read your post, no joy.
I'll run it again, w/o reboot:
```
denjohn@dell:~$ cd /lib/modules/2.6.24-17-generic/ubuntu/sound/alsa-driver/pci/hda
bash: cd: /lib/modules/2.6.24-17-generic/ubuntu/sound/alsa-driver/pci/hda: No such file or directory
denjohn@dell:~$ sudo mv snd-hda-intel.ko.REPLACEDBYhsfmodem snd-hda-intel.ko
[sudo] password for denjohn: 
mv: cannot stat `snd-hda-intel.ko.REPLACEDBYhsfmodem': No such file or directory
denjohn@dell:~$ cd /lib/modules/2.6.24-17-generic/updates
bash: cd: /lib/modules/2.6.24-17-generic/updates: No such file or directory
denjohn@dell:~$ sudo rm snd-hda-intel.ko
rm: cannot remove `snd-hda-intel.ko': No such file or directory
denjohn@dell:~$ sudo rm snd-hda-codec.ko
rm: cannot remove `snd-hda-codec.ko': No such file or directory
denjohn@dell:~$ sudo depmod -a
denjohn@dell:~$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
denjohn@dell:~$
```

As you can see, the first 5 commands resulted in 'No such file or directory', even when I ran it the first time.
Should I be substituting 19 for the 17 in the first and 3rd commands???
Thanks

---

### Post by Denny Johnson on 2008-09-07
As far as I can tell, all looks OK in the Volume Control: HDA Intel [Alsa mixer] and in Sound Preferences.
I tried substituting Alsa for Auto Detect in Sound Prefs, no joy.

---

### Post by anjilslaire on 2008-09-07
Yes, if you are on 19, you'll want to edit. The tutorial was written for 17.

---

### Post by Denny Johnson on 2008-09-07
Still no joy, I edited the first and third commands to 19. The second, fourth and fifth commands show 'No such file or directory'
??????? 
here it is before reboot:

```
denjohn@dell:~$ cd /lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/hda
denjohn@dell:/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/hda$ 
denjohn@dell:/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/hda$ sudo mv snd-hda-intel.ko.REPLACEDBYhsfmodem snd-hda-intel.ko
[sudo] password for denjohn: 
mv: cannot stat `snd-hda-intel.ko.REPLACEDBYhsfmodem': No such file or directory
denjohn@dell:/lib/modules/2.6.24-19-generic/ubuntu/sound/alsa-driver/pci/hda$ cd /lib/modules/2.6.24-19-generic/updates
denjohn@dell:/lib/modules/2.6.24-19-generic/updates$ sudo rm snd-hda-intel.ko
rm: cannot remove `snd-hda-intel.ko': No such file or directory
denjohn@dell:/lib/modules/2.6.24-19-generic/updates$ sudo rm snd-hda-codec.ko
rm: cannot remove `snd-hda-codec.ko': No such file or directory
denjohn@dell:/lib/modules/2.6.24-19-generic/updates$ sudo depmod -a
denjohn@dell:/lib/modules/2.6.24-19-generic/updates$ sudo update-initramfs -u
update-initramfs: Generating /boot/initrd.img-2.6.24-19-generic
denjohn@dell:/lib/modules/2.6.24-19-generic/updates$ 

```

---

### Post by Denny Johnson on 2008-09-07
just tried this:
```
denjohn@dell:~$ sudo /etc/init.d/alsa-utils stop 
 * Shutting down ALSA...                                                 [ OK ] 
denjohn@dell:~$ sudo rm /var/lib/alsa/asound.state 
denjohn@dell:~$ sudo /etc/init.d/alsa-utils start 
 * Setting up ALSA...                                                    [ OK ] 
denjohn@dell:~$ 

```

from here:
[http://ubuntuforums.org/showthread.php?t=906958](http://ubuntuforums.org/showthread.php?t=906958)

still no joy on my 1420n

---

### Post by Denny Johnson on 2008-09-08
FWIW. In case this helps narrow down a solution.
I just booted from kernel 2.6.22-15-generic and have sound. 

Rebooted from 2.6.24-19, still no sound.

---

