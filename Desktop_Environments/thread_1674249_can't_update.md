---
title: "can't update"
date: 2011-01-23
forum: Desktop Environments
---

### Post by zamolxis on 2011-01-23
I installed kubuntu a while back on an AMD64 3200 and hit some problems I can't solve: ran out of space on /boot & opera KEYEXPIRED.

This is a multiboot machine. I have the /boot partition on an extended ext4 /dev/sda5 which is 50 MB size which was fine when I first set it up. It seems however that it is no longer sufficient for GRUB2:

```

$ sudo apt-get upgrade
...
The following packages have been kept back:
  linux-headers-generic
The following packages will be upgraded:
...
146 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 47.5MB/141MB of archives.
After this operation, 115kB disk space will be freed.
Do you want to continue [Y/n]? 
WARNING: The following packages cannot be authenticated!
  opera
Install these packages without verification [y/N]? N
...
wget -O - http://deb.opera.com/archive.key | sudo apt-key add -
...
OK
$ sudo apt-get install debian-archive-keyring
Reading package lists... Done
Building dependency tree       
Reading state information... Done
debian-archive-keyring is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 147 not upgraded.
1 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? 
Setting up initramfs-tools (0.98.1ubuntu6) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic

gzip: stdout: No space left on device
E: mkinitramfs failure cpio 141 gzip 1
update-initramfs: failed for /boot/initrd.img-2.6.35-24-generic
dpkg: error processing initramfs-tools (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 initramfs-tools
E: Sub-process /usr/bin/dpkg returned an error code (1)
$ sudo apt-get update
...
Fetched 262B in 1s (174B/s)

W: GPG error: http://deb.opera.com stable Release: The following signatures were invalid: K
EYEXPIRED 1295781467 KEYEXPIRED 1295781467 KEYEXPIRED 1295781467
$ sudo apt-key adv --recv-keys --keyserver keyserver.ubun
tu.com 95781467
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /e
tc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --pri
mary-keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 95781467
gpg: requesting key 95781467 from hkp server keyserver.ubuntu.com
gpgkeys: key 95781467 not found on keyserver
gpg: no valid OpenPGP data found.
gpg: Total number processed: 0

$ ll /boot
total 36487
drwxr-xr-x  4 root root     1024 2011-01-23 13:56 ./
drwxr-xr-x 25 root root     4096 2011-01-23 09:26 ../
-rw-r--r--  1 root root   700477 2010-10-16 20:37 abi-2.6.35-22-generic
-rw-r--r--  1 root root   700601 2010-12-02 01:33 abi-2.6.35-24-generic
-rw-r--r--  1 root root   122604 2010-10-16 20:37 config-2.6.35-22-generic
-rw-r--r--  1 root root   122626 2010-12-02 01:33 config-2.6.35-24-generic
drwxr-xr-x  3 root root     6144 2011-01-23 09:26 grub/
-rw-r--r--  1 root root 10994569 2010-10-25 00:03 initrd.img-2.6.35-22-generic
-rw-r--r--  1 root root 10993677 2011-01-23 09:26 initrd.img-2.6.35-24-generic
drwx------  2 root root    12288 2010-10-24 20:59 lost+found/
-rw-r--r--  1 root root   165084 2010-09-24 14:16 memtest86+.bin
-rw-r--r--  1 root root   167264 2010-09-24 14:16 memtest86+_multiboot.bin
-rw-r--r--  1 root root  2342386 2010-10-16 20:37 System.map-2.6.35-22-generic
-rw-r--r--  1 root root  2343073 2010-12-02 01:33 System.map-2.6.35-24-generic
-rw-r--r--  1 root root     1335 2010-10-16 20:41 vmcoreinfo-2.6.35-22-generic
-rw-r--r--  1 root root     1336 2010-12-02 01:36 vmcoreinfo-2.6.35-24-generic
-rw-r--r--  1 root root  4336016 2010-10-16 20:37 vmlinuz-2.6.35-22-generic
-rw-r--r--  1 root root  4338064 2010-12-02 01:33 vmlinuz-2.6.35-24-generic
$ du /boot
du: cannot read directory `/boot/lost+found': Permission denied
12      /boot/lost+found
6       /boot/grub/locale
1298    /boot/grub
37775   /boot

```

I'm not too familiar with kubuntu so any suggestion would welcome. I would rather avoid formatting / repartitioning as I have a few other OSs on this multiboot machine.

---

### Post by azerttyu on 2011-01-23
Hi 

About opera problem, issue it's yet opened.
You see more information here : [http://my.opera.com/desktopteam/blog/a-second-opera-11-00-final-build-for-linux-freebsd](http://my.opera.com/desktopteam/blog/a-second-opera-11-00-final-build-for-linux-freebsd)

About other space disk, sorry i can't help.

---

### Post by Krytarik on 2011-01-23
My boot directory only consumes ca. 31 MB, also with 2 kernel versions, your files are bigger or at least consumes more space, that has nothing to do with Grub2.

The fast way would be to remove the oldest kernel via Synaptic, search for the version number, there are always three packages per kernel:
- linux-image-VERSION-generic
- linux-headers-VERSION-generic
- linux-headers-VERSION

The other way would obviously be to enlarge the partition were your boot directory is located.

---

### Post by zamolxis on 2011-01-24
> **azerttyu said:**
> Hi 

About opera problem, issue it's yet opened.
You see more information here : [http://my.opera.com/desktopteam/blog/a-second-opera-11-00-final-build-for-linux-freebsd](http://my.opera.com/desktopteam/blog/a-second-opera-11-00-final-build-for-linux-freebsd)

About other space disk, sorry i can't help.
Thank you for that pointer, it makes more sense now :)
However, should I be updating via the .deb? Not sure..

---

### Post by zamolxis on 2011-01-24
> **Krytarik said:**
> The fast way would be to remove the oldest kernel via Synaptic, search for the version number, there are always three packages per kernel:
- linux-image-VERSION-generic
- linux-headers-VERSION-generic
- linux-headers-VERSION

This Kubuntu default install does not have Synaptic, so I'll have to uninstall via aptitude, I guess. However, uninstalling the old one means essentially uninstalling the current kernel while the other kernel is not fully installed. I'll give it a try though since messing up with partitions is not something I'm happy to do now.

Thank you both for the quick reply.

---

### Post by Krytarik on 2011-01-24
Since all the relevant files are there twice, one time for subversion 2.6.35-22 and one time for 2.6.35-24, I believe the failed update is an update of the latter subversion.

You could also boot into 2.6.35-22 and remove the other subversion, if you are not sure.
Then do an upgrade again, and the subversion 2.6.35-24 gets installed fresh, without space problem.

As for the Opera issue: Although you get those warning, you could choose to install it via apt, since there is apparently just a temporary issue with the GPG security key.

---

### Post by zamolxis on 2011-01-24
for anyone else experiencing the Opera NO_PUBKey error, it is now solved by```
$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4E7532C8
```

---

### Post by zamolxis on 2011-01-24
Thank you, Krytarik. Here's what I've done:
```
$ sudo apt-get remove linux-image-2.6.35-22-generic linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  linux-generic linux-headers-2.6.35-24 linux-headers-2.6.35-24-generic
  linux-headers-generic linux-image-generic
The following packages will be REMOVED:
  linux-headers-2.6.35-22 linux-headers-2.6.35-22-generic linux-image-2.6.35-22-generic
The following NEW packages will be installed:
  linux-headers-2.6.35-24 linux-headers-2.6.35-24-generic
The following packages will be upgraded:
  linux-generic linux-headers-generic linux-image-generic
3 upgraded, 2 newly installed, 3 to remove and 149 not upgraded.
1 not fully installed or removed.
Need to get 11.1MB of archives.
After this operation, 139MB disk space will be freed.
Do you want to continue [Y/n]? 
Get:1 http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/main linux-headers-2.6.35-24 all 2.6.35-24.42 [10.3MB]
Get:2 http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/main linux-headers-2.6.35-24-generic amd64 2.6.35-24.42 [799kB]
Get:3 http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/main linux-headers-generic amd64 2.6.35.24.28 [5,026B]
Get:4 http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/main linux-generic amd64 2.6.35.24.28 [5,026B]
Get:5 http://ca.archive.ubuntu.com/ubuntu/ maverick-updates/main linux-image-generic amd64 2.6.35.24.28 [5,034B]
Fetched 11.1MB in 39s (281kB/s)                                                           
Selecting previously deselected package linux-headers-2.6.35-24.
(Reading database ... 111844 files and directories currently installed.)
Unpacking linux-headers-2.6.35-24 (from .../linux-headers-2.6.35-24_2.6.35-24.42_all.deb) ...
Selecting previously deselected package linux-headers-2.6.35-24-generic.
Unpacking linux-headers-2.6.35-24-generic (from .../linux-headers-2.6.35-24-generic_2.6.35-24.42_amd64.deb) ...
Preparing to replace linux-headers-generic 2.6.35.22.23 (using .../linux-headers-generic_2.6.35.24.28_amd64.deb) ...
Unpacking replacement linux-headers-generic ...
(Reading database ... 131430 files and directories currently installed.)
Removing linux-headers-2.6.35-22-generic ...
Removing linux-headers-2.6.35-22 ...
(Reading database ... 111848 files and directories currently installed.)
Preparing to replace linux-generic 2.6.35.22.23 (using .../linux-generic_2.6.35.24.28_amd64.deb) ...
Unpacking replacement linux-generic ...
Preparing to replace linux-image-generic 2.6.35.22.23 (using .../linux-image-generic_2.6.35.24.28_amd64.deb) ...
Unpacking replacement linux-image-generic ...
(Reading database ... 111847 files and directories currently installed.)
Removing linux-image-2.6.35-22-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-22-generic /boot/vmlinuz-2.6.35-22-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-24-generic
Found initrd image: /boot/initrd.img-2.6.35-24-generic
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
Setting up initramfs-tools (0.98.1ubuntu6) ...
update-initramfs: deferring update (trigger activated)
Setting up linux-headers-2.6.35-24 (2.6.35-24.42) ...
Setting up linux-headers-2.6.35-24-generic (2.6.35-24.42) ...
Examining /etc/kernel/header_postinst.d.
run-parts: executing /etc/kernel/header_postinst.d/nvidia-common 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
Setting up linux-headers-generic (2.6.35.24.28) ...
Setting up linux-image-generic (2.6.35.24.28) ...
Setting up linux-generic (2.6.35.24.28) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.35-24-generic
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
...
```

Looks like everything's fine. I'll probably run grub-update when the upgrade is done, followed by ```
$ sudo apt-get autoremove
``` to keep things clean.

I did not want to install synaptic as I'm trying to familiarize myself with the default KDE apps.

---

### Post by Krytarik on 2011-01-24
Looks good for me too!

Is there no native graphical package manager for KDE, or at least not pre-installed?

---

### Post by zamolxis on 2011-01-24
It looks like they integrated gDebi in the Control Panel (Settings) in lieu of Synaptic. Not bad.. ;)

---

### Post by Krytarik on 2011-01-24
> **zamolxis said:**
> It looks like they integrated gDebi in the Control Panel (Settings) in lieu of Synaptic. Not bad.. ;)
I wouldn't use Gdebi where it's avoidable, because of no update support.

---

### Post by Frogs Hair on 2011-01-24
> **zamolxis said:**
> for anyone else experiencing the Opera NO_PUBKey error, it is now solved by```
$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 4E7532C8
```

This command doesn't work for me (command not found) I will keep looking . I received and installed the Opera update and the key expired the next day . I will disable the source until I find a solution.. Thanks for posting.

I tried with the Apt Key Manager also and the key failed to import.

---

### Post by Frogs Hair on 2011-01-24
> **NhocCuteGirlUK said:**
> Hi 
 

 
About opera problem, issue it's yet opened.
 
You see more information here : [http://my.opera.com/desktopteam/blog...-linux-freebsd]("http://my.opera.com/desktopteam/blog/a-second-opera-11-00-final-build-for-linux-freebsd")
 

 
About other space disk, sorry i can't help.
__________________

Thanks , I have seen that.

---

### Post by Krytarik on 2011-01-24
> **NhocCuteGirlUK said:**
> 
About other space disk, sorry i can't help.

It's already solved, at least temporarily.

@zamolxis: Please mark this thread as solved then, you may start another thread on the Opera topic.

---

### Post by Frogs Hair on 2011-01-25
> **Krytarik said:**
> It's already solved, at least temporarily.

@zamolxis: Please mark this thread as solved then, you may start another thread on the Opera topic.

Opera topic solved . enabled the source again today and received the new key.

---

### Post by zamolxis on 2011-01-25
> **Krytarik said:**
> I wouldn't use Gdebi where it's avoidable, because of no update support.

New programs via gdebi, updates via another app. Haven't played much with that, it just works and it's configurable from Settings.

---

### Post by zamolxis on 2011-01-25
> **Frogs Hair said:**
> Opera topic solved . enabled the source again today and received the new key.

My experience was that the new Opera installed but on apt-get updates I started getting a "NoKey" error instead of KEYEXPIRED, so I used the command above to get a new key.

---

### Post by margarettefox on 2011-01-25
> **zamolxis said:**
> It looks like they integrated gDebi in the Control Panel (Settings) in lieu of Synaptic. Not bad.. ;)


yeah i agree with you.

__________
  [health insurance]("http://www.californiahealthplans.com/")

---

### Post by Krytarik on 2011-01-25
> **zamolxis said:**
> New programs via gdebi, updates via another app. Haven't played much with that, it just works and it's configurable from Settings.
Please read my earlier post in another thread regarding the packages matter:
[http://ubuntuforums.org/showthread.php?p=10235241](http://ubuntuforums.org/showthread.php?p=10235241)

---

### Post by zamolxis on 2011-01-29
It turns out that marking this as "solved" was premature.. 

It seems that I have to get Opera's key on every upgrade, again - it's not persistent on reboot. Furthermore the linux kernel is being held back and not upgraded.

```
$ sudo apt-get update
...
W: GPG error: http://deb.opera.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A2019EA84E7532C8
W: Duplicate sources.list entry http://apt.boxee.tv/ maverick/main amd64 Packages (/var/lib/apt/lists/apt.boxee.tv_dists_maverick_main_binary-amd64_Packages)
$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  linux-generic linux-headers-generic linux-image-generic
The following packages will be upgraded:
  update-manager-core update-manager-kde
2 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.

```

Also, where is the boxee key and how do I get it??

---

### Post by zamolxis on 2011-01-29
Resolved the Boxee key issue with:
```
$ wget -q "http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x07124991f766fa20" -O- | sudo apt-key add -
$ $ sudo apt-key list
/etc/apt/trusted.gpg
--------------------
...
pub   1024D/4E7532C8 2011-01-11 [expires: 2012-01-11]
uid                  Opera Software Archive Automatic Signing Key 2011 <packager@opera.com>
sub   4096g/BAC0E9D1 2011-01-11 [expires: 2012-01-11]

pub   1024D/F766FA20 2010-04-06
uid                  Tom Sella <tsella@boxee.tv>
sub   2048g/FF2ED300 2010-04-06

```

So both the Opera & Boxee key are there but so far on each reboot I get the GPG error after *apt-get update*.

The kernel updates continue to be held back.

---

### Post by Krytarik on 2011-01-29
> **zamolxis said:**
> 
The kernel updates continue to be held back.
Because there is another kernel update out now, and it may -again- be that you don't have enough space to install the new one. Try it like the other time.

I can't help you regarding the Opera key issue.

---

### Post by zamolxis on 2011-01-30
I could've forced apt-get to stop holding back packages but instead I used the Settings app to perform an update and everything eventually worked. I know had both 35-24 and 35-25.

Using autoremove got rid of the old headers, but kept the generic "image":
```
$ sudo apt-get remove linux-image-2.6.35-24-generic linux-headers-2.6.35-24-generic linux-headers-2.6.35-24
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package linux-headers-2.6.35-24 is not installed, so not removed
Package linux-headers-2.6.35-24-generic is not installed, so not removed
The following packages will be REMOVED:
  linux-image-2.6.35-24-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 139MB disk space will be freed.
Do you want to continue [Y/n]?  
(Reading database ... 125178 files and directories currently installed.)
Removing linux-image-2.6.35-24-generic ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 2.6.35-24-generic /boot/vmlinuz-2.6.35-24-generic
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-25-generic
Found initrd image: /boot/initrd.img-2.6.35-25-generic
Found memtest86+ image: /memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done
The link /vmlinuz.old is a damaged link
Removing symbolic link vmlinuz.old 
 you may need to re-run your boot loader[grub]
The link /initrd.img.old is a damaged link
Removing symbolic link initrd.img.old 
 you may need to re-run your boot loader[grub]
```

Updating seems alright; the only issue left to resolve is the ATI video, but that's a different story altogether.

Thank you Krytarik.

---

### Post by Krytarik on 2011-01-30
Do you know why the kernel packages have been kept back? Since there was obviously enough free disk space to install the new kernel, without removing 35-24 before. Also, since you removed 35-22 in post #8, there was only one kernel left, 35-24, thus definetely enough free disk space to install another kernel.

Regarding your ATI driver issue: Do you want to start another thread on this topic? I'd be glad to help you with those as well.

---

### Post by zamolxis on 2011-01-30
> **Krytarik said:**
> Do you know why the kernel packages have been kept back? No idea..

> Regarding your ATI driver issue: Do you want to start another thread on this topic? I'd be glad to help you with those as well.

I was just looking at the bug reports.. Settings / Xinerama does not save dual monitor setup and reverts to clone on reboot and not all the resolutions are available. There's a few other problems. I would've preferred to use the opensource drivers for my ATI card, but that doesn't really seem to work. I'll be filing a bug report.

---

### Post by Krytarik on 2011-01-30
OF TOPIC:

If you want to use open source drivers for your ATI cards, I recommend the Open Source Edge drivers, the should deliver a considerably better performance than the default ones:
[http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers](http://wiki.cchtml.com/index.php/Ubuntu_Lucid_Installation_Guide#Installing_Open_Source_Edge_Drivers)
[https://launchpad.net/~xorg-edgers/+archive/ppa]("https://launchpad.net/%7Exorg-edgers/+archive/ppa")
```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get upgrade

```You will need to create a proper "xorg.conf" to get your your dual monitor setup work properly, I know this guide "Nvidia" titled, just leave the "TwinView" option, and it may be necessary to set the value of "Xinerama" to "true" or "on" instead:
[https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen](https://wiki.archlinux.org/index.php/Xorg#Multiple_monitors.2FDual_screen)

If you need further help on this, please start an own thread on this topic.

---

### Post by zamolxis on 2011-02-09
here it is: [http://ubuntuforums.org/showthread.php?p=10443790](http://ubuntuforums.org/showthread.php?p=10443790)

---

