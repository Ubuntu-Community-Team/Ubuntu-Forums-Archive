---
title: "Discussion - https://help.ubuntu.com/community/MakeALiveCD/DVD/BootableFlashFromHardd"
date: 2012-06-29
forum: Documentation and Community Wiki Discussions
---

### Post by nothingspecial on 2012-06-29
Please use this thread for discussion regarding

[https://help.ubuntu.com/community/MakeALiveCD/DVD/BootableFlashFromHarddiskInstall](https://help.ubuntu.com/community/MakeALiveCD/DVD/BootableFlashFromHarddiskInstall)

Support threads should be posted in normal forums.

Thank you.

---

### Post by c4c on 2012-12-28
;)

---

### Post by itagomo on 2013-06-05
I'm now on the part "_*C. Chroot into the new system and modify it:"*_

whenever I do update, I'm getting this error


> ```
root@ubuntu:/# apt-get update

```Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424) raring Release.gpg
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424) raring Release                     
Err [http://dl.google.com](http://dl.google.com) stable Release.gpg                                                             
  Something wicked happened resolving 'dl.google.com:http' (-11 - System error)
Ign [http://dl.google.com](http://dl.google.com) stable Release                                                                 
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring Release.gpg                          
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424) raring/main i386 Packages          
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424) raring/restricted i386 Packages    
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates Release.gpg                                                
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release.gpg                                              
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424) raring/main Translation-en_US      
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424) raring/main Translation-en
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424) raring/restricted Translation-en_US
Ign cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424) raring/restricted Translation-en   
Ign [http://security.ubuntu.com](http://security.ubuntu.com) raring-security Release                                                  
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring Release                                                            
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates Release                
Err [http://dl.google.com](http://dl.google.com) stable/main i386 Packages
  Something wicked happened resolving 'dl.google.com:http' (-11 - System error)
Err [http://dl.google.com](http://dl.google.com) stable/main Translation-en_US                                                  
  Something wicked happened resolving 'dl.google.com:http' (-11 - System error)
Err [http://dl.google.com](http://dl.google.com) stable/main Translation-en                                                     
  Something wicked happened resolving 'dl.google.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main i386 Packages                                       
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted i386 Packages   
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/main Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en_US
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://security.ubuntu.com](http://security.ubuntu.com) raring-security/restricted Translation-en
  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/main Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring/restricted Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted i386 Packages
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/main Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted Translation-en_US
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) raring-updates/restricted Translation-en
  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/raring/Release.gpg)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/raring-security/Release.gpg)  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/raring-updates/Release.gpg)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)


W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg](http://dl.google.com/linux/chrome/deb/dists/stable/Release.gpg)  Something wicked happened resolving 'dl.google.com:http' (-11 - System error)


W: Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424)/dists/raring/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch cdrom://Ubuntu 13.04 _Raring Ringtail_ - Release i386 (20130424)/dists/raring/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs


W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages](http://dl.google.com/linux/chrome/deb/dists/stable/main/binary-i386/Packages)  Something wicked happened resolving 'dl.google.com:http' (-11 - System error)


W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en_US](http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en_US)  Something wicked happened resolving 'dl.google.com:http' (-11 - System error)


W: Failed to fetch [http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en](http://dl.google.com/linux/chrome/deb/dists/stable/main/i18n/Translation-en)  Something wicked happened resolving 'dl.google.com:http' (-11 - System error)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/main/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/main/binary-i386/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-i386/Packages](http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/binary-i386/Packages)  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/main/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/raring-security/main/i18n/Translation-en_US)  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/main/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/raring-security/main/i18n/Translation-en)  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/i18n/Translation-en_US](http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/i18n/Translation-en_US)  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)


W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/i18n/Translation-en](http://security.ubuntu.com/ubuntu/dists/raring-security/restricted/i18n/Translation-en)  Something wicked happened resolving 'security.ubuntu.com:http' (-11 - System error)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/raring/main/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/raring/restricted/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/main/i18n/Translation-en_US](http://archive.ubuntu.com/ubuntu/dists/raring/main/i18n/Translation-en_US)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/main/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/raring/main/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/restricted/i18n/Translation-en_US](http://archive.ubuntu.com/ubuntu/dists/raring/restricted/i18n/Translation-en_US)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring/restricted/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/raring/restricted/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/raring-updates/main/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-i386/Packages](http://archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/binary-i386/Packages)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/main/i18n/Translation-en_US](http://archive.ubuntu.com/ubuntu/dists/raring-updates/main/i18n/Translation-en_US)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/main/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/raring-updates/main/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/i18n/Translation-en_US](http://archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/i18n/Translation-en_US)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)


W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/i18n/Translation-en](http://archive.ubuntu.com/ubuntu/dists/raring-updates/restricted/i18n/Translation-en)  Something wicked happened resolving 'archive.ubuntu.com:http' (-11 - System error)


E: Some index files failed to download. They have been ignored, or old ones used instead.

can't find any fix

---

### Post by Kamil_Jwiak on 2013-09-14
Hi there.

I need some help with creating bootable CD/DVD based on installed version of Ubuntu.

The last step ends with the error on my machine.
> 
[SIZE=4]_*E. Build the CD/DVD*_[/SIZE]
1. Make the ISO file
```
sudo grub-mkrescue -o ~/live-cd.iso ${CD}
```

```
grub-mkrescue -o 
```
seems to be not available anymore so I was trying to use --output, but then I get en error
```
sudo grub-mkrescue --output=~/ISO.iso ${CD}
```

> 
Enabling BIOS support ...
Using MULTIBOO.000;1 for /tmp/grub-mkrescue.xaZXtfoLhU/boot/grub/i386-pc/multiboot2.mod (multiboot.mod)
Using GCRY_SHA.000;1 for /tmp/grub-mkrescue.xaZXtfoLhU/boot/grub/i386-pc/gcry_sha1.mod (gcry_sha256.mod)
Using GCRY_SHA.001;1 for /tmp/grub-mkrescue.xaZXtfoLhU/boot/grub/i386-pc/gcry_sha256.mod (gcry_sha512.mod)
Using PASSWORD.000;1 for /tmp/grub-mkrescue.xaZXtfoLhU/boot/grub/i386-pc/password.mod (password_pbkdf2.mod)
Using SEARCH_F.000;1 for /tmp/grub-mkrescue.xaZXtfoLhU/boot/grub/i386-pc/search_fs_file.mod (search_fs_uuid.mod)
grub-mkisofs: Unable to open disc image file
: No such file or directory



According to [kababbaro post]("http://ubuntuforums.org/showthread.php?t=688872&page=32&p=11549686#post11549686") i have changed chmod to +r recursively to all files.
I doesn't change anything. I still get error message posted above.

Can you help me fix this issue?
I'm using /usr/bin/grub-mkrescue (GNU GRUB 1.98-1ubuntu13) on Ubuntu 10.04 32-bit.

Best Regards,
Kamil

---

### Post by Slippy Lane on 2013-10-05
I found the answer [here]("https://help.ubuntu.com/community/LiveCDCustomizationFromScratch")

Specifically - after mounted dev, proc and sys, but before chroot, I did this:

(I've modified it to fit the guide we're following)

> sudo cp /etc/hosts $WORK/rootfs/etc/hosts
sudo rm $WORK/rootfs/etc/resolv.conf
sudo cp /etc/resolv.conf $WORK/rootfs/etc/resolv.conf
sudo cp /etc/apt/sources.list $WORK/rootfs/etc/apt/sources.list


After doing all that, I chrooted into $WORK/rootfs and the apt-get update and all following steps worked first time.

Hope that helps

---

### Post by majedaly on 2014-03-13
Thanks for the extensive information. I tried using the steps described in the wiki, faced the following issues:
1- Unable to connect to internet from the chroot inveronment, which could be overcome by editing resolv.conf and adding a name server
2- During the creation of the CD I get the following warnings:
df: Warning: cannot read table of mounted file systems: No such file or directory
cryptsetup: WARNING: could not determine root device from /etc/fstab
I checked /etc/fstab which appears to be empty.
I completed the steps, ignoring the warnings, and created a live USB stick. it boots normally, but asks for login.
I tried the same username and password used during creation , the root username and password, and user ubuntu with blank password nothing worked.
I repeated the steps, and created a user under the chroot environment , also didn't work
I tried logging in by pressing ALT+F1 but the system doesn't even give the login prompt, it shows authentication error.
I am using Ubuntu 13.10. I tried the same process on a totally different Ubuntu system, with the same result. The ISO file is created, and booting, but asks for a username and password.
I tried even resetting the user password totally under the chroot environment, also didn't work.
Appreciate any help
Thanks

---

### Post by miker_alpha on 2014-03-25
> **majedaly said:**
> Thanks for the extensive information. I tried using the steps described in the wiki, faced the following issues:
1- Unable to connect to internet from the chroot inveronment, which could be overcome by editing resolv.conf and adding a name server
2- During the creation of the CD I get the following warnings:
df: Warning: cannot read table of mounted file systems: No such file or directory
cryptsetup: WARNING: could not determine root device from /etc/fstab
I checked /etc/fstab which appears to be empty.
I completed the steps, ignoring the warnings, and created a live USB stick. it boots normally, but asks for login.
I tried the same username and password used during creation , the root username and password, and user ubuntu with blank password nothing worked.
I repeated the steps, and created a user under the chroot environment , also didn't work
I tried logging in by pressing ALT+F1 but the system doesn't even give the login prompt, it shows authentication error.
I am using Ubuntu 13.10. I tried the same process on a totally different Ubuntu system, with the same result. The ISO file is created, and booting, but asks for a username and password.
I tried even resetting the user password totally under the chroot environment, also didn't work.
Appreciate any help
Thanks

At the stage when you remove non-system users, instead of "998" in the command, use "1000" - that will leave the original installation user defined. Then edit /etc/password (still under chroot)
check for a user with UIC=999 -- there should not be one
In the line defining the user with UIC=1000 edit out the field that defines the password; it should originally be <colon>x<colon> , change it to :: . That user can login with no password. Login at a TTY to create a home directory, e.g.  "sudo mkdir /home/<username> && sudo chown <username>:<username> /home/<username> . You can then complete a graphic login.

---

### Post by darklordpaunik8880 on 2014-06-05
Hello any one  and thank you  for this  tutorial!!
I was thinking  if it is possible to  create another tutorial  on how to add  grub splash 
i mean to customize  the grub  menu  with custom image..  :)please let me know if it is possible..!!
sorry for my bad  english!!

---

### Post by Nobody Nessie on 2014-06-22
Thank you for the whole "topics and wiki". I was looking for something like this for a few weeks to build a more secure and anonymous version of the last Ubuntu. I assumed that a fresh and updated installation of the 14.04 LTS, with only a few needed desktop applications (LibreOffice, GIMP, VLC) and all the needed Internet applications, transmission-GTK, VPN, Tor, Jondo, (and ALL Internet accessing applications getting their enforce Apparmor profiles), some kernel hardening tips and all unnecessary applications and services removed, could give something possibly better than Tails or Whonix (for my own use). In fact, all I need is already on my OS, the only thing I would add for security reason is to build it as a live-CD to avoid it to be hacked.The probability of getting hacked once with a pre-securised live-CD like this is already one thing. Still using this pre-securised live-CD, then the probability of getting hacked twice (with the same exploit, probably) begins to be really an exploit ! (literal meaning). And the possible damages should be closed to nothing, that means the ratio used resources / caused damages would be surely close to be a nonsense.

This is something I still have somewhere in mind as an experiment. I do not know if I will try it one day. Are those topics and wiki updated ? I have seen that remastersys (that seemed to be very efficient to this kind of tasks) is no longer available, for example ?

---

### Post by thedeco on 2015-06-04
Before I issue the command:
sudo chroot ${WORK}/rootfs /bin/bash
If I don't do this I don't have DNS in the chroot:
sudo rm [COLOR=#333333][FONT=UbuntuMono]${WORK}/rootfs/etc/resolv.conf
sudo cp /etc/resolv.conf [/FONT][/COLOR][COLOR=#333333][FONT=UbuntuMono]${WORK}/rootfs/etc/

when I run
[/FONT][/COLOR]apt-get install casper lupin-casper[COLOR=#333333][FONT=UbuntuMono]I get a message:
[/FONT][/COLOR]df: Warning: cannot read table of mounted file systems: No such file or directory[COLOR=#333333][FONT=UbuntuMono]
[/FONT][/COLOR]E: Can not write log (Is /dev/pts mounted?) - openpty (2: No such file or directory)

I had to do [COLOR=#FF0000][FONT=Arial]sudo mount --bind /dev/pts [/FONT][/COLOR][COLOR=#333333][FONT=UbuntuMono]${WORK}/rootfs[/FONT][/COLOR][COLOR=#FF0000][FONT=Arial]/dev/pts[/FONT][/COLOR]

After update-initramfs -u -k $(uname -r):df: Warning: cannot read table of mounted file systems: No such file or directory
cryptsetup: WARNING: could not determine root device from /etc/fstab

[COLOR=#333333][FONT=UbuntuMono]


[/FONT][/COLOR]

---

### Post by matan4 on 2015-08-18
hello ,
i tried to create custom image to Ubuntu 14.4 and i didnt succeeded  
can someone help me with guide to ubuntu server 2014 cli version 
thank you !!!

---

### Post by pete45 on 2015-10-06
I also experienced a number of the same errors.
I imagine these procedures/scripts have not been updated for newer distros...

I've unfortunately spent a lot of time trying to make this work - but obviously a gamble with antiquated tutorials.
It seems this would be a very desirable feature for many Linux users.

Many great efforts in the past, but no one is maintaining... (Remastersys and similar)
This would be so useful for duplicating a desired environment - but running from RAM via squashfs.

Perhaps I'll try some hybrid approach from these instructions and the UCK approach...

---

### Post by asafmgn on 2015-12-07
hello and thanks for this wonderful  tutorial .
in the latest boot cd of lubuntu 15.10 there is the possibility to change keymap before the boot cd load . (see attached screenshot) 
how do i also add it to this custom cd i'm creating with your tutorial?
is it possible?

---

### Post by jkarurosu on 2016-03-17
Hi, 

After executing the command "update-initramfs -u -k $(uname -r)" I got a warning saying "df: Warning: cannot read table of mounted file systems: No such file or directory", I'm using a 14.04 distro, below the details.

Description:    Ubuntu 14.04.2 LTS
Release:        14.04
Codename:       trusty

Does anyone have seen this issue before?

Regards,

---

### Post by David_Partridge on 2018-05-02
I just ran through this with my system again as I recently updated from kernel 4.8.17 to 4.15.0-15-generic on the "strong" suggestion of the btrfs team.

I get the following messages when I try to boot the CD:

/init: . : line 261: can't open /scripts/casper
kernel panic - not syncing: Attempted to kill init!

Help!!!

Thanks
David

---

