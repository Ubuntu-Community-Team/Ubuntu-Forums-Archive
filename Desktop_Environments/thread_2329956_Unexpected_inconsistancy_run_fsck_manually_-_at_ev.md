---
title: "Unexpected inconsistancy run fsck manually - at every boot. Ubuntu 16.04"
date: 2016-07-06
forum: Desktop Environments
---

### Post by Calum_Mackenzie on 2016-07-06
I have encountered a problem with the file system on my machine;
 "Unexpected inconsistancy run fsck manually" This message appears every time I boot-up my machine. 

I believe that this may possibly be a known bug in 16.04? and is caused by a problem with the clock/Date being wrong / going wrong?

I have managed to get my machine through "grub" to the Shell Command feature and Opened the "root Drop to root shell prompt" I then took the option "Press Enter for maintenance " & have entered my password in preparation for the next step..................But what is the next step?

I would be very grateful if anyone can advise on how to proceed with the recovery process?
n.b I have ubuntu 16.04 on a usb stick as an "iso file" should it be required as part of the recovery process.

---

### Post by QDR06VV9 on 2016-07-06
Once you're dropped to the shell (i.e. "(Repair Filesystem) 1#"), type in 
```
fsck /dev/sda2 
```
assuming your root partition is on sda2. Reboot after that and tell me what happens.

---

### Post by Bashing-om on 2016-07-06
Calum_Mackenzie; runrickus

16.04 == systemd

You can also force fsck at boot time by passing fsck.mode=force, as a kernel parameter. This will check every filesystem you have on the machine.


[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by Calum_Mackenzie on 2016-07-07
Response to fsck /dev/sdal 

fsck from until - Linux 2.27.1
fsck 1.42.13 (17 May-2015)
fsck.ext2: Attempt to read block from filesystem resulted in short read while trying to open /dev/sdal
Could this be a zero-length partition?

---

### Post by mcduck on 2016-07-07
The last character in the partitions name is always a number. Looks like you have lower case L there, while it probably should be number 1 instead...

---

### Post by Calum_Mackenzie on 2016-07-07
Hi Bashing-om,

Can you please expand & explain the procedure which you mention.

---

### Post by Bashing-om on 2016-07-07
Calum_Mackenzie; Sure !

Boot the install to the grub boot menu -> with an ubuntu kernel selected to boot -> press the 'e' key for edit mode;
Boot parameters screen, here arrow down to the line starting with linux and containing the terms "quiet splash" ;
Insert the term " fsck.mode=force " inplace of quiet splash such that now you also see the boot messages;
key combo ctl+x to continue the boot process .

All there is to it, the system will run the file system checks - and will attempt simple fixes - prior to mounting the devices. If there is a continued problem, fsck will so advise.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Calum_Mackenzie on 2016-07-07
Hi Bashing-om,

I have done as suggested & recieved a long list of code! 
To save time I have taken a picture of the screen which shows all the code responses & attaching it, so the response can be seen.

"Boot the install to the grub boot menu -> with an ubuntu kernel selected to boot -> press the 'e' key for edit mode;Boot parameters screen, here arrow down to the line starting with linux and containing the terms "quiet splash" ;
Insert the term " fsck.mode=force " inplace of quiet splash such that now you also see the boot messages;
key combo ctl+x to continue the boot process .


All there is to it, the system will run the file system checks - and will attempt simple fixes - prior to mounting the devices. If there is a continued problem, fsck will so advise."


[ATTACH=CONFIG]270005[/ATTACH]

---

### Post by Bashing-om on 2016-07-07
Calum_Mackenzie; Yuk ;

Not enough there to tell what is going on.
What happens now when re-booting ?

[INDENT][INDENT]maybe, not so yes
[/INDENT][/INDENT]

---

### Post by Calum_Mackenzie on 2016-07-07
UPDATE: now I have had time to copy & write the code from the screen - it is as below.
```

[   0.943178]   [<c102c862>]  timer_interrupt+0×12/0×20
[   0.943244]   [<c10c9f66>]   handle_irq_event_percpu+0×86/0×1c0
[   0.943309]   [<c10ca0cf>]   handle_edge_irq+0×6d/0×120
[   0.943435]   [<c10ccfe0>]   handle_level_irq+0xe0/0xe0xe0
[   0.943500]   <IRQ>     [<c17aacdc>]  _do_softirq+0×5f/0×260
[   0.934674]   [<c17aa173>]   common_interrupt+0×33/0×38
[   0.934744]   [<c10748a0>]   ? _do_softirq+0×5f/0×260
[   0.934806]   [<c10748a0>]   ? cpu_callback+0×1d0/0×1d0
[   0.934868]   [<c102c2f8>]    do_softring_own_stack+0×28/0×38
[   0.934932]   <IRQ>     [<c1074c75>]   irq_exit+0×a5/0×b0
[   0.944049]   [<c17aad98>]   smp_apic _ timer_interupt +0×34/0×3c
[   0.944110]   [<c17aa478>]   apic _ timer_interupt + 0×34/0×3c
[   0.944176]   [<c116f9ad>]    ?  panic+0×16e/0×1af
[   0.944241]   [<c1b79061>]   mount_block_root+0×199/0×20
[   0.944303]   [<c1b79210>]   mount_root+0×63/0×68
[   0.944371]   [<c1b7935a>]   prepare_namespace+0×145/0×176
[   0.944439]   [<c1b78d8a>]   kernel_init_+freeable+0×1b1/0×1d0
[   0.944513]   [<c179fcf0>]     kernel_init+0×10/0xe0
[   0.944580]   [<c1099431>]   ?  schedule_tail+0×11/0×50
[   0.944650]   [<c17a9949>]   ret_from_kernel_thread+0×21/0×38
[   0.944718]   [<c179fce0>]    ?  rest_init+0×70/0×70
[   0.944783] ---[  end trace b3d2df61bb937d79 ]---
```

---

### Post by Bashing-om on 2016-07-07
Calum_Mackenzie; Hey;

I just do not see an indication of a problem ( not withstanding "---[ end trace b3d2df61bb937d79 ]-".

Did the file system check run ? What results now when re-booting ?


[INDENT][INDENT]got to have something to work with
[/INDENT][/INDENT]

---

### Post by Calum_Mackenzie on 2016-07-08
I have Rebooted - No change & no further ahead. However when the black screen with the flashing line top left appeared I did not push the Space Bar which would take the machine to the GNU GRUB screen, instead I left it to run so I could capture the information that appears on that screen - which is the attached picture,which will hopefully offer up more clues as to what is going on with the machine.


[ATTACH=CONFIG]270008[/ATTACH]

---

### Post by Bashing-om on 2016-07-08
Calum_Mackenzie; Ouch !

Input/output errors say we best be looking at the health of the drive !
What does smartctl say about the drive ?
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
[http://ubuntuforums.org/showthread.php?t=2192335](http://ubuntuforums.org/showthread.php?t=2192335)
[http://smartmontools.sourceforge.net/badblockhowto.html](http://smartmontools.sourceforge.net/badblockhowto.html)

As if the medium is inconsistent, the file system also will be.

[INDENT][INDENT]Houston we have a problem
[/INDENT][/INDENT]

---

### Post by wildmanne39 on 2016-07-08
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Calum_Mackenzie on 2016-07-09
Have tried Smartontools, but they are not installed, Also looked at the link to the page on ubuntu forums and what was said there about using Smartontools, but alas nothing.

---

### Post by Bashing-om on 2016-07-09
Calum_Mackenzie; Ouch !

Input/output errors say we best be looking at the health of the drive !
What does smartctl say about the drive ?
[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)
[http://ubuntuforums.org/showthread.php?t=2192335](http://ubuntuforums.org/showthread.php?t=2192335)
[http://smartmontools.sourceforge.net/badblockhowto.html](http://smartmontools.sourceforge.net/badblockhowto.html)

To install the tool:
```

sudo apt install smartmontools

```

As if the medium is inconsistent, the file system also will be.

[INDENT][INDENT][/INDENT][/INDENT]

---

### Post by Calum_Mackenzie on 2016-07-10
I have tried from GNU GRUB - pressing c for command when the grub first flashed up
sudo apt install smartmontools

However 'sudo' is not recognised


However in an act of frustration! I decided to press "upstart" when in the advanced option of grub, this started a screen showing what appeared to be some sort of an attempt at starting ubuntu, left to run, lines of code started to appear in red & white, upon reading through this screen, I noted an option to press "F" to attempt repair, naturally I took the option & all sorts of code started appearing changing colour between read & white,this process completed & asked if I wanted to reboot, which I duly did & it came back to the grub screen, thinking I was on to something, I went to repeat the process from "upstart" BUT instead of repeating the previous, A screen appeared & hung for minute as if ubuntu was trying to start & it did! Ubuntu then proceeded to download a massive update, which took about 10 minutes, which installed, machine was restarted & everything appears normal.

---

### Post by Calum_Mackenzie on 2016-07-10
I do have a related query to my machine crashing;

Having now got my machine back working & installed a massive update, I notice that I have another 2 updates..........What is troubling me is, these same 2 updates kept appearing & not installing for days on end prior to my machine crashing - I cannot but help wondering since there appeared to be a problem installing these updates, if I should attempt installing them again? 

```
 3.20.1+git20160617.1.0440874.ubuntu-xenial-0ubuntu1~16.04.1

  * Backport to 16.04, with the world's longest version number.
  * Update Vcs-Bzr for the stable release

3.20.1+git20160617.1.0440874.ubuntu-xenial-0ubuntu1

  * New upstream snapshot from the wip/ubuntu-xenial branch at
    git://git.gnome.org/gnome-software.
    - Fix launching various KDE4 applications (LP: #1575529)
    - Guard against review server errors (LP: #1590508)
    - Fix a couple of CSS errors (LP: #1590508)
    - Fix conversion from star ratings (1-5) to G-S rating (0-100) (LP: #1581938)
    - Fix wilson score calulation (LP: #1581938)
    - Make the app folder dialog work again (LP: #1590115)
    - Remove broken symlink of xdg-app-reviews plugin (LP: #1573052)
    - Disable redundant notification (LP: #1592382)
    - Disable app folders feature when run outside GNOME (LP: #1590152)
  * Drop snap_mime_type.patch which is in this release. 
```





```
 3.20.1+git20160617.1.0440874.ubuntu-xenial-0ubuntu1~16.04.1

  * Backport to 16.04, with the world's longest version number.
  * Update Vcs-Bzr for the stable release

3.20.1+git20160617.1.0440874.ubuntu-xenial-0ubuntu1

  * New upstream snapshot from the wip/ubuntu-xenial branch at
    git://git.gnome.org/gnome-software.
    - Fix launching various KDE4 applications (LP: #1575529)
    - Guard against review server errors (LP: #1590508)
    - Fix a couple of CSS errors (LP: #1590508)
    - Fix conversion from star ratings (1-5) to G-S rating (0-100) (LP: #1581938)
    - Fix wilson score calulation (LP: #1581938)
    - Make the app folder dialog work again (LP: #1590115)
    - Remove broken symlink of xdg-app-reviews plugin (LP: #1573052)
    - Disable redundant notification (LP: #1592382)
    - Disable app folders feature when run outside GNOME (LP: #1590152)
  * Drop snap_mime_type.patch which is in this release. 
```

---

### Post by Bashing-om on 2016-07-10
Calum_Mackenzie; Well, well ..

Just goes to show, never can tell ... In many cases 'buntu can be self healing .., particularly so with "updates" .

Not having context, I can not advise on what the git packages are .

To get a current status of the package management system, run:
```

sudo apt update
sudo apt upgrade
sudo apt -f install
sudo dpkg -C

```
If there are reported errors. Post the complete output, and we consider opening a new thread on this new issue .

Good things do hapen

---

### Post by Calum_Mackenzie on 2016-07-10
Hi, i have run the commands above and it appears that I have 3 updates installed are no longer required and have used suggested code that appeared to remove them - However I am a little concerned about Restarting to finally remove the files because of this warning *"Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported."*


user@user-ThinkPad-X61s:~$ sudo dkpg -C
[sudo] password for user: 
sudo: dkpg: command not found
user@user-ThinkPad-X61s:~$ sudo apt update
```
Hit:1 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) xenial InRelease
Hit:2 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial InRelease                  
Get:3 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates InRelease [94.5 kB]   
Get:4 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-backports InRelease [92.2 kB] 
Get:5 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/main i386 Packages [244 kB]
Hit:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) xenial-security InRelease              
Get:7 [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) xenial-updates/universe i386 Packages [149 kB] 
```

Fetched 579 kB in 1s (322 kB/s)                          
Reading package lists... Done
Building dependency tree       
Reading state information... Done
3 packages can be upgraded. Run 'apt list --upgradable' to see them.
Listing... Done

```
gnome-software/xenial-updates 3.20.1+git20160617.1.0440874.ubuntu-xenial-0ubuntu1~16.04.1 i386 [upgradable from: 3.20.1+git20160426.1.a976144-ubuntu-xenial-0ubuntu1]
gnome-software-common/xenial-updates 3.20.1+git20160617.1.0440874.ubuntu-xenial-0ubuntu1~16.04.1 all [upgradable from: 3.20.1+git20160426.1.a976144-ubuntu-xenial-0ubuntu1]
ubuntu-software/xenial-updates 3.20.1+git20160617.1.0440874.ubuntu-xenial-0ubuntu1~16.04.1 i386 [upgradable from: 3.20.1+git20160426.1.a976144-ubuntu-xenial-0ubuntu1] 
```

user@user-ThinkPad-X61s:~$ sudo apt -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-4.4.0-22 linux-headers-4.4.0-22-generic linux-image-4.4.0-22-generic linux-image-extra-4.4.0-22-generic
Use 'sudo apt autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 3 not to upgrade.
user@user-ThinkPad-X61s:~$ ```
 sudo apt autoremove
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  ```
linux-headers-4.4.0-22 linux-headers-4.4.0-22-generic linux-image-4.4.0-22-generic linux-image-extra-4.4.0-22-generic
```

0 to upgrade, 0 to newly install, 4 to remove and 3 not to upgrade.
After this operation, 237 MB disk space will be freed.
Do you want to continue? [Y/n] Y
(Reading database ... 623698 files and directories currently installed.)

```
Removing linux-headers-4.4.0-22-generic (4.4.0-22.40) ...
Removing linux-headers-4.4.0-22 (4.4.0-22.40) ...
Removing linux-image-extra-4.4.0-22-generic (4.4.0-22.40) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
update-initramfs: Generating /boot/initrd.img-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/unattended-upgrades 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
```

Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.

```
Found linux image: /boot/vmlinuz-4.4.0-28-generic
Found initrd image: /boot/initrd.img-4.4.0-28-generic
Found linux image: /boot/vmlinuz-4.4.0-24-generic
Found initrd image: /boot/initrd.img-4.4.0-24-generic
Found linux image: /boot/vmlinuz-4.4.0-22-generic
Found initrd image: /boot/initrd.img-4.4.0-22-generic
Found linux image: /boot/vmlinuz-3.19.0-59-generic
Found initrd image: /boot/initrd.img-3.19.0-59-generic
Found linux image: /boot/vmlinuz-3.19.0-58-generic
Found initrd image: /boot/initrd.img-3.19.0-58-generic
Found linux image: /boot/vmlinuz-3.19.0-56-generic
Found initrd image: /boot/initrd.img-3.19.0-56-generic
Found linux image: /boot/vmlinuz-3.19.0-51-generic
Found initrd image: /boot/initrd.img-3.19.0-51-generic
Found linux image: /boot/vmlinuz-3.19.0-49-generic
Found initrd image: /boot/initrd.img-3.19.0-49-generic
Found linux image: /boot/vmlinuz-3.19.0-47-generic
Found initrd image: /boot/initrd.img-3.19.0-47-generic
Found linux image: /boot/vmlinuz-3.19.0-43-generic
Found initrd image: /boot/initrd.img-3.19.0-43-generic
Found linux image: /boot/vmlinuz-3.19.0-42-generic
Found initrd image: /boot/initrd.img-3.19.0-42-generic
Found linux image: /boot/vmlinuz-3.19.0-41-generic
Found initrd image: /boot/initrd.img-3.19.0-41-generic
Found linux image: /boot/vmlinuz-3.19.0-39-generic
Found initrd image: /boot/initrd.img-3.19.0-39-generic
Found linux image: /boot/vmlinuz-3.19.0-37-generic
Found initrd image: /boot/initrd.img-3.19.0-37-generic
Found linux image: /boot/vmlinuz-3.19.0-33-generic
Found initrd image: /boot/initrd.img-3.19.0-33-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin 
```
done

```
Removing linux-image-4.4.0-22-generic (4.4.0-22.40) ...
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
update-initramfs: Deleting /boot/initrd.img-4.4.0-22-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 4.4.0-22-generic /boot/vmlinuz-4.4.0-22-generic
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-4.4.0-28-generic
Found initrd image: /boot/initrd.img-4.4.0-28-generic
Found linux image: /boot/vmlinuz-4.4.0-24-generic
Found initrd image: /boot/initrd.img-4.4.0-24-generic
Found linux image: /boot/vmlinuz-3.19.0-59-generic
Found initrd image: /boot/initrd.img-3.19.0-59-generic
Found linux image: /boot/vmlinuz-3.19.0-58-generic
Found initrd image: /boot/initrd.img-3.19.0-58-generic
Found linux image: /boot/vmlinuz-3.19.0-56-generic
Found initrd image: /boot/initrd.img-3.19.0-56-generic
Found linux image: /boot/vmlinuz-3.19.0-51-generic
Found initrd image: /boot/initrd.img-3.19.0-51-generic
Found linux image: /boot/vmlinuz-3.19.0-49-generic
Found initrd image: /boot/initrd.img-3.19.0-49-generic
Found linux image: /boot/vmlinuz-3.19.0-47-generic
Found initrd image: /boot/initrd.img-3.19.0-47-generic
Found linux image: /boot/vmlinuz-3.19.0-43-generic
Found initrd image: /boot/initrd.img-3.19.0-43-generic
Found linux image: /boot/vmlinuz-3.19.0-42-generic
Found initrd image: /boot/initrd.img-3.19.0-42-generic
Found linux image: /boot/vmlinuz-3.19.0-41-generic
Found initrd image: /boot/initrd.img-3.19.0-41-generic
Found linux image: /boot/vmlinuz-3.19.0-39-generic
Found initrd image: /boot/initrd.img-3.19.0-39-generic
Found linux image: /boot/vmlinuz-3.19.0-37-generic
Found initrd image: /boot/initrd.img-3.19.0-37-generic
Found linux image: /boot/vmlinuz-3.19.0-33-generic
Found initrd image: /boot/initrd.img-3.19.0-33-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
done 
```
user@user-ThinkPad-X61s:~$

---

### Post by Bashing-om on 2016-07-10
Calum_Mackenzie; Ouch;

Well 2 problems that I see:
the software Center wants to upgrade .. but it is 32 bit packaging .. Huh ??? WHY ???
what returns: - Between Code Tags - to maintain readability
code tag tutorial:
[http://ubuntuforums.org/showthread.p...8#post12776168](http://ubuntuforums.org/showthread.p...8#post12776168)

```

apt-cache policy gnome-software gnome-software-common ubuntu-software

```
and seems we have a conflict of interest between gnome-software and ubuntu-software.

Why are all those old kernels hanging about ? 'autoremove' should have dealt with them .., as it did not we have a problem.
show 
```

dpkg -l | grep linux
ls -al /boot

```
so we see what we can do.

As to the advisory: " Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported." it can be safely ignored IF you want .. but it is easily fixed with the proper edit to the /etc/default/grub file.
to whit:
> 
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=10

once the file is saved .. must run:
```

sudo update-grub

```
to propagate the change to the operating system.

a conflict of interest of this nature
we may get deep here .

---

### Post by Calum_Mackenzie on 2016-07-11
There is no response to the suggestion 

"[I]As to the advisory: " Setting GRUB_TIMEOUT to a non-zero value when  GRUB_HIDDEN_TIMEOUT is set is no longer supported." it can be safely  ignored IF you want .. but it is easily fixed with the proper edit to  the /etc/default/grub file.
to whit:
Code:
```
GRUB_DEFAULT=0
```
```
#GRUB_HIDDEN_TIMEOUT=0
```
```
GRUB_HIDDEN_TIMEOUT_QUIET=false
```
```
GRUB_TIMEOUT=10
```
once the file is saved .. must run:
Code:
sudo update-grub
to propagate the change to the operating system.[/I]"

user@user-ThinkPad-X61s:~$ ```
GRUB_DEFAULT=0 
```
user@user-ThinkPad-X61s:~$ ```
#GRUB_HIDDEN_TIMEOUT=0
```
user@user-ThinkPad-X61s:~$```
 GRUB_HIDDEN_TIMEOUT_QUIET=false
```
user@user-ThinkPad-X61s:~$ ```
GRUB_TIMEOUT=10
```



The response to ```
 dpkg -l | grep linux
ls -al /boot 
``` is as per below

user@user-ThinkPad-X61s:~$ ```
 dpkg -l | grep linux
ii  console-setup-linux                        1.108ubuntu15                                               all          Linux specific part of console-setup
ii  libselinux1:i386                           2.4-3build2                                                 i386         SELinux runtime shared libraries
ii  libv4l-0:i386                              1.10.0-1                                                    i386         Collection of video4linux support libraries
ii  libv4lconvert0:i386                        1.10.0-1                                                    i386         Video4linux frame format conversion library
ii  linux-base                                 4.0ubuntu1                                                  all          Linux image base package
ii  linux-firmware                             1.157.2                                                     all          Firmware for Linux kernel drivers
ii  linux-generic                              4.4.0.28.30                                                 i386         Complete Generic Linux kernel and headers
ii  linux-generic-lts-vivid                    4.4.0.28.30                                                 i386         Complete Generic Linux kernel and headers (dummy transitional package)
ii  linux-headers-3.19.0-33                    3.19.0-33.38~14.04.1                                        all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-33-generic            3.19.0-33.38~14.04.1                                        i386         Linux kernel headers for version 3.19.0 on 32 bit x86 SMP
ii  linux-headers-3.19.0-37                    3.19.0-37.42~14.04.1                                        all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-37-generic            3.19.0-37.42~14.04.1                                        i386         Linux kernel headers for version 3.19.0 on 32 bit x86 SMP
ii  linux-headers-3.19.0-39                    3.19.0-39.44~14.04.1                                        all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-39-generic            3.19.0-39.44~14.04.1                                        i386         Linux kernel headers for version 3.19.0 on 32 bit x86 SMP
ii  linux-headers-3.19.0-41                    3.19.0-41.46~14.04.2                                        all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-41-generic            3.19.0-41.46~14.04.2                                        i386         Linux kernel headers for version 3.19.0 on 32 bit x86 SMP
ii  linux-headers-3.19.0-42                    3.19.0-42.48~14.04.1                                        all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-42-generic            3.19.0-42.48~14.04.1                                        i386         Linux kernel headers for version 3.19.0 on 32 bit x86 SMP
ii  linux-headers-3.19.0-43                    3.19.0-43.49~14.04.1                                        all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-43-generic            3.19.0-43.49~14.04.1                                        i386         Linux kernel headers for version 3.19.0 on 32 bit x86 SMP
ii  linux-headers-3.19.0-47                    3.19.0-47.53~14.04.1                                        all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-47-generic            3.19.0-47.53~14.04.1                                        i386         Linux kernel headers for version 3.19.0 on 32 bit x86 SMP
ii  linux-headers-3.19.0-49                    3.19.0-49.55~14.04.1                                        all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-49-generic            3.19.0-49.55~14.04.1                                        i386         Linux kernel headers for version 3.19.0 on 32 bit x86 SMP
ii  linux-headers-3.19.0-51                    3.19.0-51.58~14.04.1                                        all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-51-generic            3.19.0-51.58~14.04.1                                        i386         Linux kernel headers for version 3.19.0 on 32 bit x86 SMP
ii  linux-headers-3.19.0-56                    3.19.0-56.62~14.04.1                                        all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-56-generic            3.19.0-56.62~14.04.1                                        i386         Linux kernel headers for version 3.19.0 on 32 bit x86 SMP
ii  linux-headers-3.19.0-58                    3.19.0-58.64~14.04.1                                        all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-58-generic            3.19.0-58.64~14.04.1                                        i386         Linux kernel headers for version 3.19.0 on 32 bit x86 SMP
ii  linux-headers-3.19.0-59                    3.19.0-59.66~14.04.1                                        all          Header files related to Linux kernel version 3.19.0
ii  linux-headers-3.19.0-59-generic            3.19.0-59.66~14.04.1                                        i386         Linux kernel headers for version 3.19.0 on 32 bit x86 SMP
ii  linux-headers-4.4.0-24                     4.4.0-24.43                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-24-generic             4.4.0-24.43                                                 i386         Linux kernel headers for version 4.4.0 on 32 bit x86 SMP
ii  linux-headers-4.4.0-28                     4.4.0-28.47                                                 all          Header files related to Linux kernel version 4.4.0
ii  linux-headers-4.4.0-28-generic             4.4.0-28.47                                                 i386         Linux kernel headers for version 4.4.0 on 32 bit x86 SMP
ii  linux-headers-generic                      4.4.0.28.30                                                 i386         Generic Linux kernel headers
rc  linux-image-3.19.0-25-generic              3.19.0-25.26~14.04.1                                        i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-3.19.0-33-generic              3.19.0-33.38~14.04.1                                        i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-3.19.0-37-generic              3.19.0-37.42~14.04.1                                        i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-3.19.0-39-generic              3.19.0-39.44~14.04.1                                        i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-3.19.0-41-generic              3.19.0-41.46~14.04.2                                        i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-3.19.0-42-generic              3.19.0-42.48~14.04.1                                        i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-3.19.0-43-generic              3.19.0-43.49~14.04.1                                        i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-3.19.0-47-generic              3.19.0-47.53~14.04.1                                        i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-3.19.0-49-generic              3.19.0-49.55~14.04.1                                        i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-3.19.0-51-generic              3.19.0-51.58~14.04.1                                        i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-3.19.0-56-generic              3.19.0-56.62~14.04.1                                        i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-3.19.0-58-generic              3.19.0-58.64~14.04.1                                        i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-3.19.0-59-generic              3.19.0-59.66~14.04.1                                        i386         Linux kernel image for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-4.4.0-22-generic               4.4.0-22.40                                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-24-generic               4.4.0-24.43                                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-4.4.0-28-generic               4.4.0-28.47                                                 i386         Linux kernel image for version 4.4.0 on 32 bit x86 SMP
rc  linux-image-extra-3.19.0-25-generic        3.19.0-25.26~14.04.1                                        i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-extra-3.19.0-33-generic        3.19.0-33.38~14.04.1                                        i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-extra-3.19.0-37-generic        3.19.0-37.42~14.04.1                                        i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-extra-3.19.0-39-generic        3.19.0-39.44~14.04.1                                        i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-extra-3.19.0-41-generic        3.19.0-41.46~14.04.2                                        i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-extra-3.19.0-42-generic        3.19.0-42.48~14.04.1                                        i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-extra-3.19.0-43-generic        3.19.0-43.49~14.04.1                                        i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-extra-3.19.0-47-generic        3.19.0-47.53~14.04.1                                        i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-extra-3.19.0-49-generic        3.19.0-49.55~14.04.1                                        i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-extra-3.19.0-51-generic        3.19.0-51.58~14.04.1                                        i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-extra-3.19.0-56-generic        3.19.0-56.62~14.04.1                                        i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-extra-3.19.0-58-generic        3.19.0-58.64~14.04.1                                        i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
ii  linux-image-extra-3.19.0-59-generic        3.19.0-59.66~14.04.1                                        i386         Linux kernel extra modules for version 3.19.0 on 32 bit x86 SMP
rc  linux-image-extra-4.4.0-22-generic         4.4.0-22.40                                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-24-generic         4.4.0-24.43                                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-extra-4.4.0-28-generic         4.4.0-28.47                                                 i386         Linux kernel extra modules for version 4.4.0 on 32 bit x86 SMP
ii  linux-image-generic                        4.4.0.28.30                                                 i386         Generic Linux kernel image
ii  linux-libc-dev:i386                        4.4.0-28.47                                                 i386         Linux Kernel Headers for development
ii  linux-sound-base                           1.0.25+dfsg-0ubuntu5                                        all          base package for ALSA and OSS sound systems
ii  pptp-linux                                 1.8.0-1                                                     i386         Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                   3:6.03+dfsg-11ubuntu1                                       i386         collection of bootloaders (DOS FAT and NTFS bootloader)
ii  syslinux-common                            3:6.03+dfsg-11ubuntu1                                       all          collection of bootloaders (common)
ii  syslinux-legacy                            2:3.63+dfsg-2ubuntu8                                        i386         Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                 2.27.1-6ubuntu3.1                                           i386         miscellaneous system utilities 
```
user@user-ThinkPad-X61s:~$ ```
 ls -al /boot 
```
total 453404
```
drwxr-xr-x  3 root root     4096 Jul 10 19:55 .
drwxr-xr-x 22 root root     4096 Jul 10 10:45 ..
-rw-r--r--  1 root root  1267818 Nov  6  2015 abi-3.19.0-33-generic
-rw-r--r--  1 root root  1267820 Nov 23  2015 abi-3.19.0-37-generic
-rw-r--r--  1 root root  1267820 Dec  2  2015 abi-3.19.0-39-generic
-rw-r--r--  1 root root  1267894 Dec  8  2015 abi-3.19.0-41-generic
-rw-r--r--  1 root root  1267894 Dec 18  2015 abi-3.19.0-42-generic
-rw-r--r--  1 root root  1267894 Dec 31  2015 abi-3.19.0-43-generic
-rw-r--r--  1 root root  1267894 Jan 18 17:39 abi-3.19.0-47-generic
-rw-r--r--  1 root root  1268033 Jan 22 13:03 abi-3.19.0-49-generic
-rw-r--r--  1 root root  1268122 Feb 26 23:43 abi-3.19.0-51-generic
-rw-r--r--  1 root root  1268259 Mar 11 12:44 abi-3.19.0-56-generic
-rw-r--r--  1 root root  1268633 Mar 18 20:54 abi-3.19.0-58-generic
-rw-r--r--  1 root root  1268900 May 13 20:12 abi-3.19.0-59-generic
-rw-r--r--  1 root root  1235916 Jun  8 21:44 abi-4.4.0-24-generic
-rw-r--r--  1 root root  1236124 Jun 24 12:48 abi-4.4.0-28-generic
-rw-r--r--  1 root root   182025 Nov  6  2015 config-3.19.0-33-generic
-rw-r--r--  1 root root   182025 Nov 23  2015 config-3.19.0-37-generic
-rw-r--r--  1 root root   182025 Dec  2  2015 config-3.19.0-39-generic
-rw-r--r--  1 root root   182043 Dec  8  2015 config-3.19.0-41-generic
-rw-r--r--  1 root root   182043 Dec 18  2015 config-3.19.0-42-generic
-rw-r--r--  1 root root   182043 Dec 31  2015 config-3.19.0-43-generic
-rw-r--r--  1 root root   182043 Jan 18 17:39 config-3.19.0-47-generic
-rw-r--r--  1 root root   182043 Jan 22 13:03 config-3.19.0-49-generic
-rw-r--r--  1 root root   182043 Feb 26 23:43 config-3.19.0-51-generic
-rw-r--r--  1 root root   182043 Mar 11 12:44 config-3.19.0-56-generic
-rw-r--r--  1 root root   182043 Mar 18 20:54 config-3.19.0-58-generic
-rw-r--r--  1 root root   182043 May 13 20:12 config-3.19.0-59-generic
-rw-r--r--  1 root root   192987 Jun  8 21:44 config-4.4.0-24-generic
-rw-r--r--  1 root root   192976 Jun 24 12:48 config-4.4.0-28-generic
drwxr-xr-x  5 root root     4096 Jul 10 19:56 grub
-rw-r--r--  1 root root 19384485 Nov 23  2015 initrd.img-3.19.0-33-generic
-rw-r--r--  1 root root 19384243 Dec  2  2015 initrd.img-3.19.0-37-generic
-rw-r--r--  1 root root 19384648 Dec  5  2015 initrd.img-3.19.0-39-generic
-rw-r--r--  1 root root 19383562 Dec 17  2015 initrd.img-3.19.0-41-generic
-rw-r--r--  1 root root 19385880 Dec 21  2015 initrd.img-3.19.0-42-generic
-rw-r--r--  1 root root 19385383 Jan  6  2016 initrd.img-3.19.0-43-generic
-rw-r--r--  1 root root 19384689 Jan 21 08:14 initrd.img-3.19.0-47-generic
-rw-r--r--  1 root root 19389244 Feb 19 08:34 initrd.img-3.19.0-49-generic
-rw-r--r--  1 root root 19387535 Feb 27 09:27 initrd.img-3.19.0-51-generic
-rw-r--r--  1 root root 19387230 Mar 25 11:39 initrd.img-3.19.0-56-generic
-rw-r--r--  1 root root 19401804 Apr 13 10:37 initrd.img-3.19.0-58-generic
-rw-r--r--  1 root root 30548533 Jun  7 13:50 initrd.img-3.19.0-59-generic
-rw-r--r--  1 root root 35403245 Jul 10 10:35 initrd.img-4.4.0-24-generic
-rw-r--r--  1 root root 35410104 Jul 10 10:47 initrd.img-4.4.0-28-generic
-rw-r--r--  1 root root   182704 Jan 28 12:44 memtest86+.bin
-rw-r--r--  1 root root   184380 Jan 28 12:44 memtest86+.elf
-rw-r--r--  1 root root   184840 Jan 28 12:44 memtest86+_multiboot.bin
-rw-------  1 root root  2882197 Nov  6  2015 System.map-3.19.0-33-generic
-rw-------  1 root root  2882674 Nov 23  2015 System.map-3.19.0-37-generic
-rw-------  1 root root  2882674 Dec  2  2015 System.map-3.19.0-39-generic
-rw-------  1 root root  2882852 Dec  8  2015 System.map-3.19.0-41-generic
-rw-------  1 root root  2882852 Dec 18  2015 System.map-3.19.0-42-generic
-rw-------  1 root root  2882852 Dec 31  2015 System.map-3.19.0-43-generic
-rw-------  1 root root  2882852 Jan 18 17:39 System.map-3.19.0-47-generic
-rw-------  1 root root  2883769 Jan 22 13:03 System.map-3.19.0-49-generic
-rw-------  1 root root  2884115 Feb 26 23:43 System.map-3.19.0-51-generic
-rw-------  1 root root  2884357 Mar 11 12:44 System.map-3.19.0-56-generic
-rw-------  1 root root  2884895 Mar 18 20:55 System.map-3.19.0-58-generic
-rw-------  1 root root  2885087 May 13 20:12 System.map-3.19.0-59-generic
-rw-------  1 root root  3078872 Jun  8 21:44 System.map-4.4.0-24-generic
-rw-------  1 root root  3082234 Jun 24 12:48 System.map-4.4.0-28-generic
-rw-------  1 root root  6196576 Nov  6  2015 vmlinuz-3.19.0-33-generic
-rw-------  1 root root  6196704 Nov 23  2015 vmlinuz-3.19.0-37-generic
-rw-------  1 root root  6196704 Dec  2  2015 vmlinuz-3.19.0-39-generic
-rw-------  1 root root  6196256 Dec  8  2015 vmlinuz-3.19.0-41-generic
-rw-------  1 root root  6196096 Dec 18  2015 vmlinuz-3.19.0-42-generic
-rw-------  1 root root  6196096 Dec 31  2015 vmlinuz-3.19.0-43-generic
-rw-------  1 root root  6196128 Jan 18 17:39 vmlinuz-3.19.0-47-generic
-rw-------  1 root root  6198816 Jan 22 13:03 vmlinuz-3.19.0-49-generic
-rw-------  1 root root  6200784 Feb 26 23:43 vmlinuz-3.19.0-51-generic
-rw-------  1 root root  6202656 Mar 11 12:44 vmlinuz-3.19.0-56-generic
-rw-------  1 root root  6211136 Mar 18 20:54 vmlinuz-3.19.0-58-generic
-rw-------  1 root root  6211008 May 13 20:12 vmlinuz-3.19.0-59-generic
-rw-------  1 root root  6764032 Jun  8 21:44 vmlinuz-4.4.0-24-generic
-rw-------  1 root root  6771872 Jun 24 12:48 vmlinuz-4.4.0-28-generic 
```
user@user-ThinkPad-X61s:~$ 

The response to ```
sudo update-grub 
```

user@user-ThinkPad-X61s:~$ ```
 sudo update-grub 
```
[sudo] password for user: 
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.

```
Found linux image: /boot/vmlinuz-4.4.0-28-generic
Found initrd image: /boot/initrd.img-4.4.0-28-generic
Found linux image: /boot/vmlinuz-4.4.0-24-generic
Found initrd image: /boot/initrd.img-4.4.0-24-generic
Found linux image: /boot/vmlinuz-3.19.0-59-generic
Found initrd image: /boot/initrd.img-3.19.0-59-generic
Found linux image: /boot/vmlinuz-3.19.0-58-generic
Found initrd image: /boot/initrd.img-3.19.0-58-generic
Found linux image: /boot/vmlinuz-3.19.0-56-generic
Found initrd image: /boot/initrd.img-3.19.0-56-generic
Found linux image: /boot/vmlinuz-3.19.0-51-generic
Found initrd image: /boot/initrd.img-3.19.0-51-generic
Found linux image: /boot/vmlinuz-3.19.0-49-generic
Found initrd image: /boot/initrd.img-3.19.0-49-generic
Found linux image: /boot/vmlinuz-3.19.0-47-generic
Found initrd image: /boot/initrd.img-3.19.0-47-generic
Found linux image: /boot/vmlinuz-3.19.0-43-generic
Found initrd image: /boot/initrd.img-3.19.0-43-generic
Found linux image: /boot/vmlinuz-3.19.0-42-generic
Found initrd image: /boot/initrd.img-3.19.0-42-generic
Found linux image: /boot/vmlinuz-3.19.0-41-generic
Found initrd image: /boot/initrd.img-3.19.0-41-generic
Found linux image: /boot/vmlinuz-3.19.0-39-generic
Found initrd image: /boot/initrd.img-3.19.0-39-generic
Found linux image: /boot/vmlinuz-3.19.0-37-generic
Found initrd image: /boot/initrd.img-3.19.0-37-generic
Found linux image: /boot/vmlinuz-3.19.0-33-generic
Found initrd image: /boot/initrd.img-3.19.0-33-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin 
```
done

---

### Post by Bashing-om on 2016-07-11
Calum_Mackenzie; Hey;

Regret that my instructions were not the more explicit.
The :
> 
GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=10

is not a set of terminal commands... but an edit to the file /etc/default/grub .
Standard operating procedure is to make a backup prior to any edit to any file. Make the backup; terminal command:
```

sudo cp /etc/default/grub  /etc/default/grub-11jul2016

``` such that if any thing adverse happens, one can restore the original file.
Make it so as above, including the commented line (#):
```

sudo -H gedit /etc/default/grub

```
where you are to open the file in the text editor "gedit" with administrative authority in a GUI ( sudo -H) - IF gedit is the editor that you have installed - and make the edits .
once your file lines are as above, save the file in the text editor.
Now tell the system a change to this file has been made;
```

sudo update-grub

```

My little mind deals with one issue at a time .. here the edit to the file;
Once this is done we change focus to remove the old kernels on this system.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Calum_Mackenzie on 2016-07-14
Re - Back-up; I have Déjà Dup Backup Tool installed - But it does not get a good review, so never used it. What would be the recommendation of the Ubuntu community be regarding a programme / back-up tool? 

Also would you back-up to USB or online?

---

### Post by Bashing-om on 2016-07-15
Calum_Mackenzie; Welp ...

I do not use ANY backup app - why, when all system files are on the install medium.
All I DO backup - in 3 places - is my personal files AND I do keep a change log of all changes I make to the install.

If you have a large amount of personal files to backup .. might be that the rsync command will be of interest to you .

[INDENT][INDENT]KISS
[INDENT][INDENT][INDENT]is my attitude
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Calum_Mackenzie on 2016-07-20
> **Bashing-om said:**
> Calum_Mackenzie; Hey;

Regret that my instructions were not the more explicit.
The :

is not a set of terminal commands... but an edit to the file /etc/default/grub .
Standard operating procedure is to make a backup prior to any edit to any file. Make the backup; terminal command:
```

sudo cp /etc/default/grub  /etc/default/grub-11jul2016

``` such that if any thing adverse happens, one can restore the original file.
Make it so as above, including the commented line (#):
```

sudo -H gedit /etc/default/grub

```
where you are to open the file in the text editor "gedit" with administrative authority in a GUI ( sudo -H) - IF gedit is the editor that you have installed - and make the edits .
once your file lines are as above, save the file in the text editor.
Now tell the system a change to this file has been made;
```

sudo update-grub

```

My little mind deals with one issue at a time .. here the edit to the file;
Once this is done we change focus to remove the old kernels on this system.
[INDENT][INDENT]ain't nothing but a thing
[/INDENT]
[/INDENT]


**_RESPONSE TO ABOVE IS AS PER BELOW:-_**

user@user-ThinkPad-X61s:~$ ```
 sudo cp /etc/default/grub  /etc/default/grub-11jul2016 
```
[sudo] password for user: 
user@user-ThinkPad-X61s:~$ ```
 sudo cp /etc/default/grub  /etc/default/grub-11jul2016 
```
user@user-ThinkPad-X61s:~$ ```
sudo -H gedit /etc/default/grub 
```


# If you change this file, run 'update-grub' afterwards to update
#```
 /boot/grub/grub.cfg. 
```
# For full documentation of the options in this file, see:
# ```
  info -f grub -n Simple configuration 
```

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#```
GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
```

# Uncomment to disable graphical terminal (grub-pc only)
#```
GRUB_TERMINAL=console
```

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#```
GRUB_GFXMODE=640x480
```

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#```
GRUB_DISABLE_LINUX_UUID=true
```

# Uncomment to disable generation of recovery mode menu entries
#```
GRUB_DISABLE_RECOVERY="true"
```

# Uncomment to get a beep at grub start
#```
GRUB_INIT_TUNE="480 440 1"
```
```
GRUB_GFXPAYLOAD_LINUX=None
```

[U][B]
WHAT IS ADVICE NOW ON HOW TO PROCEED BASED ON ABOVE INFORMATION?[/B][/U]

---

### Post by Bashing-om on 2016-07-20
Calum_Mackenzie; Huh ??

What have you done ??
That last is more than my little mind can keep up with .. 
All I directed was a simple edit to the file.
Show us now what that file is:
```

cat /etc/default/grub

```

Do the other 2 problems still exist ?

[INDENT][INDENT]I try to Keep It Simple
[/INDENT][/INDENT]

---

### Post by Calum_Mackenzie on 2016-07-21
# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
GRUB_GFXPAYLOAD_LINUX=None
user@user-ThinkPad-X61s:~$

---

### Post by Bashing-om on 2016-07-21
Calum_Mackenzie; Hey ....


My communications skills are poor, and perhaps not up to this task.

What I need to know is that the config file /etc/default/grub is in a consistent state prior to doing anything else.
To that end I want to see that complete file .. and that output needs to be within code tags .. to maintain and promote readability.
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

Show me the complete file:
```

cat /etc/default/grub

```

Then we verify the sysyem status

---

### Post by Calum_Mackenzie on 2016-07-21
[SIZE=3][B][U]Response to code suggested is copied / pasted & changed to code where lines of code are identifiable 
[/U][/B][I]
 Suggestion = ```
cat /etc/default/grub
``` [/I]


# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#```
GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"
```

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command ```
 `vbeinfo' 
```
#```
GRUB_GFXMODE=640x480 
```

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#```
GRUB_DISABLE_LINUX_UUID=true 
```

# Uncomment to disable generation of recovery mode menu entries
#```
GRUB_DISABLE_RECOVERY="true"
```

# Uncomment to get a beep at grub start
#```
GRUB_INIT_TUNE="480 440 1" 
```
```
GRUB_GFXPAYLOAD_LINUX=None 
```
user@user-ThinkPad-X61s:~$ [/SIZE]

---

### Post by Bashing-om on 2016-07-21
Calum_Mackenzie; Noooo ...

example of what I want to see:
```

sysop@1404mini:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=false
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR="My-Work-14.04"
GRUB_CMDLINE_LINUX_DEFAULT="text"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
GRUB_GFXMODE=1600x900

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
sysop@1404mini:~$

```
where this is my file .. and modified to suit my own use case .. do not duplicate !

[INDENT]if at 1st you do not succeed
[INDENT][INDENT][INDENT]try try again.
[/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by Calum_Mackenzie on 2016-07-21
[SIZE=3]Below is a straight copy & paste in response to     "[/SIZE]*[SIZE=3]cat /etc/default/grub[/SIZE]*[SIZE=3]"


```
user@user-ThinkPad-X61s:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
GRUB_GFXPAYLOAD_LINUX=None
user@user-ThinkPad-X61s:~$ 
```[/SIZE]

---

### Post by Bashing-om on 2016-07-21
Calum_Mackenzie; Ouch !

That hurts my eyes . 
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
Please, please comply .. makes what we do the easier .. what we do is tough enough as is .

A start to understand grub:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

As to your file:
1)
> 
GRUB_HIDDEN_TIMEOUT=0

comment this line out, make it like:
```

#GRUB_HIDDEN_TIMEOUT=0

```
as it is no longer supported.
2)
> 
GRUB_HIDDEN_TIMEOUT_QUIET=true

change to false, make it like:
```

GRUB_HIDDEN_TIMEOUT_QUIET=false

```
3)
> 
GRUB_GFXPAYLOAD_LINUX=None

is an invalid variable none; see: [https://www.gnu.org/software/grub/manual/html_node/gfxmode.html#gfxmode](https://www.gnu.org/software/grub/manual/html_node/gfxmode.html#gfxmode)

Once the edits have been done; save the file and run terminal command:
```

sudo update-grub

``` to propagate the change to the operating system.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by Calum_Mackenzie on 2016-07-21
user@user-ThinkPad-X61s:~$ ```
GRUB_HIDDEN_TIMEOUT_QUIET=false
```
user@user-ThinkPad-X61s:~$```
GRUB_GFXPAYLOAD_LINUX=None
``` 
user@user-ThinkPad-X61s:~$ ```
sudo update-grub
```

```
[sudo] password for user:

Generating grub configuration file ...

Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.

Found linux image:
 /boot/vmlinuz-4.4.0-31-generic

Found initrd image:
 /boot/initrd.img-4.4.0-31-generic

Found linux image:
 /boot/vmlinuz-4.4.0-28-generic

Found initrd image:
 /boot/initrd.img-4.4.0-28-generic

Found linux image:
/boot/vmlinuz-4.4.0-24-generic

Found initrd image:
 /boot/initrd.img-4.4.0-24-generic

Found linux image:
 /boot/vmlinuz-3.19.0-59-generic

Found initrd image:
 /boot/initrd.img-3.19.0-59-generic

Found linux image:
/boot/vmlinuz-3.19.0-58-generic

Found initrd image:
 /boot/initrd.img-3.19.0-58-generic

Found linux image:
 /boot/vmlinuz-3.19.0-56-generic

Found initrd image:
 /boot/initrd.img-3.19.0-56-generic

Found linux image:
 /boot/vmlinuz-3.19.0-51-generic

Found initrd image:
 /boot/initrd.img-3.19.0-51-generic

Found linux image:
 /boot/vmlinuz-3.19.0-49-generic

Found initrd image:
 /boot/initrd.img-3.19.0-49-generic

Found linux image:
 /boot/vmlinuz-3.19.0-47-generic

Found initrd image:
 /boot/initrd.img-3.19.0-47-generic

Found linux image:
/boot/vmlinuz-3.19.0-43-generic

Found initrd image:
 /boot/initrd.img-3.19.0-43-generic

Found linux image:
 /boot/vmlinuz-3.19.0-42-generic

Found initrd image:
 /boot/initrd.img-3.19.0-42-generic

Found linux image:
 /boot/vmlinuz-3.19.0-41-generic

Found initrd image:
 /boot/initrd.img-3.19.0-41-generic

Found linux image:
 /boot/vmlinuz-3.19.0-39-generic

Found initrd image:
 /boot/initrd.img-3.19.0-39-generic

Found linux image:
 /boot/vmlinuz-3.19.0-37-generic

Found initrd image:
 /boot/initrd.img-3.19.0-37-generic

Found linux image:
 /boot/vmlinuz-3.19.0-33-generic

Found initrd image:
 /boot/initrd.img-3.19.0-33-generic

Found memtest86+ image:
 /boot/memtest86+.elf

Found memtest86+ image:
 /boot/memtest86+.bin

done
user@user-ThinkPad-X61s:~$ 
```

---

### Post by Bashing-om on 2016-07-21
Calum_Mackenzie; Yuk ...

I am having a great deal of difficulty following your logic.
These are simple edits, I do not understand why you do not understand .
Where is our failure to communicate ? 
Be aware English is the only language I am able to communicate in .
Open the file for editing with administrative authority:
```

sudo -H gedit /etc/default/grub

``` Or whatever you have for a text editor on your system.
Make your /etc/default/grub file exactly as:
[code]
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
# info -f grub -n 'Simple configuration'

---

### Post by Calum_Mackenzie on 2016-07-22
I am not sure why this machine does not respond to command codes given? OR behave in a manner expected. 
I have entered the various codes as as suggested / posted - then in turn I have posted the responses which I have received / as appears on my screen, then in turn I break these down into individual boxes to display each code in it's own separate box in a chronological order in which the responses appeared. 

For instance the response received to ***"sudo update-grub" ***is exactly as per below - the machine does nothing except generate response code - it does **_not _**run any updates or change anything

_***1. I enter the code as can be seen below***_
user@user-ThinkPad-X61s:~$ [/code]sudo update-grub[/code]
[I][B]
_2. System asks for password - which is entered_[/B][/I]
[sudo] password for user: 
[U][I][B]
3. System says that it is generating grub configuration file[/B][/I][/U]
Generating grub configuration file ...
[U]
4. ***Code response to command*** [B][I]"sudo update-grub" appears on screen
[/I][/B][/U]
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
```
Found linux image: /boot/vmlinuz-4.4.0-31-generic
Found initrd image: /boot/initrd.img-4.4.0-31-generic
Found linux image: /boot/vmlinuz-4.4.0-28-generic
Found initrd image: /boot/initrd.img-4.4.0-28-generic
Found linux image: /boot/vmlinuz-4.4.0-24-generic
Found initrd image: /boot/initrd.img-4.4.0-24-generic
Found linux image: /boot/vmlinuz-3.19.0-59-generic
Found initrd image: /boot/initrd.img-3.19.0-59-generic
Found linux image: /boot/vmlinuz-3.19.0-58-generic
Found initrd image: /boot/initrd.img-3.19.0-58-generic
Found linux image: /boot/vmlinuz-3.19.0-56-generic
Found initrd image: /boot/initrd.img-3.19.0-56-generic
Found linux image: /boot/vmlinuz-3.19.0-51-generic
Found initrd image: /boot/initrd.img-3.19.0-51-generic
Found linux image: /boot/vmlinuz-3.19.0-49-generic
Found initrd image: /boot/initrd.img-3.19.0-49-generic
Found linux image: /boot/vmlinuz-3.19.0-47-generic
Found initrd image: /boot/initrd.img-3.19.0-47-generic
Found linux image: /boot/vmlinuz-3.19.0-43-generic
Found initrd image: /boot/initrd.img-3.19.0-43-generic
Found linux image: /boot/vmlinuz-3.19.0-42-generic
Found initrd image: /boot/initrd.img-3.19.0-42-generic
Found linux image: /boot/vmlinuz-3.19.0-41-generic
Found initrd image: /boot/initrd.img-3.19.0-41-generic
Found linux image: /boot/vmlinuz-3.19.0-39-generic
Found initrd image: /boot/initrd.img-3.19.0-39-generic
Found linux image: /boot/vmlinuz-3.19.0-37-generic
Found initrd image: /boot/initrd.img-3.19.0-37-generic
Found linux image: /boot/vmlinuz-3.19.0-33-generic
Found initrd image: /boot/initrd.img-3.19.0-33-generic
Found memtest86+ image: /boot/memtest86+.elf
Found memtest86+ image: /boot/memtest86+.bin
```

done
[U][I][B]5. End of code response to command given

6. Machine prepares for next command[/B][/I][/U]
user@user-ThinkPad-X61s:~$ 


[U][I][B]
RESPONSE STRING TO NEXT SUGGESTED COMMAND     [/B][/I][/U][I][B][SIZE=3]"sudo -H gedit /etc/default/grub"


[/SIZE][/B][/I] 
[SIZE=3][U][I][B]1. Above Code is entered as can be seen immeadeteley below
[/B][/I][/U][/SIZE]
user@user-ThinkPad-X61s:~$ sudo -H gedit /etc/default/grub

[SIZE=3]_***2. Machine asks for password & it is duly entered***_[/SIZE]

[sudo] password for user: 


[SIZE=3][U][I][B]3. Code response appears on a seperate screen - again machine does not actually do anything in response to the code other than generate a code response - as per below
[/B][/I][/U][/SIZE]
```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
GRUB_GFXPAYLOAD_LINUX=None
```

---

### Post by QDR06VV9 on 2016-07-22
@ Calum_Mackenzie Bashing-om has not abandoned you we are having a few issues in some functions of the forum ATM
So hang in here he will be back Bigger and Better than ever:)
Regards

---

### Post by Bashing-om on 2016-07-23
test. this is just a test.

---

### Post by Bashing-om on 2016-07-23
Calum_Mackenzie; Hey ...

Now that I have access restored to this thread .. show me now what we have to work with.

I desire to see that complete file .. and only that file.
Post back the output of terminal command:
```

cat /etc/default/grub

```
I do need to know that the file is proper before we can do anything else.

[INDENT][INDENT]i is easy. once you have done it.
[/INDENT][/INDENT]

---

### Post by Calum_Mackenzie on 2016-07-24
```
user@user-ThinkPad-X61s:~$ cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"
GRUB_GFXPAYLOAD_LINUX=None
user@user-ThinkPad-X61s:~$
```

---

### Post by Bashing-om on 2016-07-24
Calum_Mackenzie; Ouch !

Still not made the edits as directed. please see my Private Message and comply with making the edits and and and 
provide the requested output - all in one paste of:
```

cat /etc/default/grub

```
Once this file is in a consistent state and I KNOW it is .. then and only then can we proceed.

[INDENT][INDENT]stepping up
[INDENT][INDENT]on that curve of learning
[/INDENT][/INDENT][/INDENT][/INDENT]

---

