---
title: "Ubuntu 10.10; error: file not found. Grub rescue&gt;-"
date: 2010-09-16
forum: Dell Ubuntu Support (CLOSED)
---

### Post by spc456 on 2010-09-16
I have a Dell Inspiron 1545 with Windows 7.

I installed Ubuntu 10.07, rebooted few times and all went well.

However, after stating Windows 7 I could no longer get the system to boot.

I saw a post from Colin Watson and he mention that I should render GRUB2 unbootable to see if Win 7 boots;
I don't know how to do that.

I goggled about the subject and there are 1000's of posting; difficult to find what I need since no post match my case.

Last night I tried all things that are on the postings but still just a black screen with same GRUB's error message.

I even installed Ubuntu 10.10 pre-released and no luck.

Most of the commands that are posted on various documentations do not work:

Here is how my system looks like:

(Booting from Live CD)

$ sudo fdisk -l

/dev/sda1   13    102400 de Dell Utility 
/dev/sda2 * 13    1926 15360000 7 HPFS/NTFS 
/dev/sda3   1926  30892 232676566 7 HPFS/NTFS 
/dev/sda4   30893 60802 240245761 5 Extended 
/dev/sda5   30893 59584 230467584 83 Linux 
/dev/sda6   59585 60802 9777152 82 Linux swap / Solaris 

$ sudo mount /dev/sda2 /mnt

$ sudo grub-install --root-directory=/mnt/ /dev/sda

reboot

But after rebooting all of what it shows is a black screen with the GRUB error:

error: file not found. 
Grub rescue>-

If I type 

$ sudo update-grub 

after booting with live CD I get:

$ /usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted)

I think /dev is mounted.
$ sudo mount --bind /dev/pts  /mnt/dev/pts does not work

$ sudo mount --bind /proc /mnt/proc does not work

$ sudo mount --bind /sys  /mnt/sys does not work

$ sudo chroot /mnt does not work

I checked /mnt for proc, sys, dev, dev/pts and they don't exist.

Should I mount /mnt to /dev/sda5 where linux is installed?
So far I have been mounting on /dev/sda2; the boot partition.
Someone mention in this forum that Dell corrupts the GRUB files in 
the boot partition, if so how can I prevent it.
I can not get to Windows since the system does not boot. 
Right now the only way I can boot is with Ubuntu live CD.

I am stuck ](*,) .

Mark

---

### Post by drs305 on 2010-09-16
Mark,

The boot flag isn't used by Ubuntu/Linux. Your Ubuntu install is on sda5, so that is the one you want to mount.

From a LiveCD Desktop terminal:
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```

I don't know specifically what Dell does, but the above should get Ubuntu back.

---

### Post by spc456 on 2010-09-16
Thank you drs305 (Thomas Jefferson)

I am away from my laptop now but tonight I will mount /mnt to /dev/sda5

Hopefully this will get me to boot.

Thank you for your response,

Mark :p

---

### Post by drs305 on 2010-09-16
I forgot to welcome you to the Ubuntu forums - so welcome!  :-)

The commands I provided should correctly install Grub2, and when you reboot Grub should find Windows. If it doesn't, open a terminal and run 
sudo update-grub

If your Windows install still isn't seen, you can take a look at this guide, which helps when Grub2 overwrites something needed by Windows.
[How to restore the Ubuntu/XP/Vista/7 bootloader ]("http://ubuntuforums.org/showthread.php?t=1014708")

If the problem is Dell specific, I probably can't be of much use.

Posting the contents of the results of this script by *meierfra* might help someone who is familiar with Dell products and knows how their setup works.
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

---

### Post by spc456 on 2010-09-17
Thank you drs305.

The instruction you gave me worked well and I got u-10.10 to boot.

I want to thank you for pointing out that I should mount /mnt to /dev/sda5 where Linux was installed. I had the impression that it had to be mounted on the boot partition.

I rebooted u-10.10 and updated grub:

u-10_10@u-10.10-laptop:~$ sudo update-grub
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.35-21-generic
Found initrd image: /boot/initrd.img-2.6.35-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found memtest86+ multiboot image: /boot/memtest86+_multiboot.bin
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory
done

I am not sure what lines 7 and 8 means:
ls: cannot access /var/lib/os-prober/mount/boot
Boot: No such file or directory.

As you already suspected Win 7 was not listed in the grub2 booting list, so I will follow your instructions on "How to restore the Ubuntu/XP/Vista/7 bootloader "

The mystery is why did Windows 7 messed up grub2 loader; it was working fine until I decided to boot on Windows 7.

Somehow my installation of Ubuntu 10.10 did not activated the sound system. I installed lots of sound applications and tested but still no sound.
I wonder if it is because Ubuntu 10.10 is a pre-release and all drivers are not there yet. 
Sound worked fine under Ubuntu 10.04.

Thank you again :)

Mark

---

### Post by drs305 on 2010-09-17
spc456,

First, I'm glad you got Ubuntu to boot. 

After you boot to W7 - I've heard a few reports of W7 overwriting the MBR just by using it. I don't use W7 so I really don't have more information about it. So if you suddenly can't use Ubuntu again and haven't changed anything except that you've booted to Windows, that might be the issue.

I think the error line you mentioned may have to do with having an extra file called "boot" or "Boot" somewhere on your drive. I've seen other posts with a similar message. You can search these forums for that exact error message and possible solution.

Maverick is beta, so there are bound to be some issues for some users. The sound in Maverick I believe is intentionally muted on start up. Make sure the sound icon at the top right of the top panel does not have "--", which means it's muted. If it is, double click and turn up the volume. By default you will have to do this each time you start the Beta.  If that isn't the problem, the best thing to do if you can't find posts to help is to open a new thread in the Maverick testing forurm.

Hope you get these issues cleared up quickly!

---

### Post by spc456 on 2010-09-20
Hello drs305

This is a follow-up of my problems with Ubuntu 10.04 and 10.10 Grub2 booting: 

I wasn't able to boot into W7 with the instructions in "How to restore the Ubuntu/XP/Vista/7 bootloader".

Again I got the error:

error: file not found. 
Grub rescue>-

Then I booted with live CD and fixed with
Code:
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

(sda5 is where Linux was installed)

Grud2 booted right into u-10.10.
Ubuntu 10.10 is pre-release so I could not get the sound to work.
I went back to u-10.04.

I still cannot boot to W7, but at least I have u-10.04 :) .
I will keep on looking for ways to get to W7.

Thank you.

Mark

---

### Post by drs305 on 2010-09-21
Mark,

I'm glad you got at least Ubuntu working again. W7 really *should* be found by Grub2 and boot.  I don't know anything about Win7. I would suggest you do a search of these forums - the answer is here somewhere. 

Otherwise, open a new thread, explain the W7 problem you are having, and in the original post place the contents of the RESULTS.txt created with the bootinfo script found here:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")

When you paste the contents, place them between "code" tags, which you generate by pressing the # icon in the post's menubar.

I suspect some of the W7 boot files are missing. The boot info script will provide the information necessary for our helpers to identify them and suggest how to get them back.

---

### Post by spc456 on 2010-09-21
drs305,

Thank you for the follow-up.
Your last suggestion  [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)  has hit the nail on the head: Tons of information generated by boot_info_script055.sh on RESULTS.txt.        
The problem appears to be the duplicate installation of Grub2.
Earlier I inadvertently installed Grub2 on partition sda2. (See #1 above). I misinterpreted the instructions, it was wrong to install Grub2 on the boot partition sda2. That partition is Win7 /Boot/BCD but I didn&#8217;t know then. Please see the listing of RESULTS.txt below.

Now I have a question: which way is the best way to remove /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img from sda2 without screwing up further? 

Thank you again.

Mark

PS: Also I want to thank the people at [http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)  for boot_info_script055.sh
      It revealed the problem in my boot system.
PSS. Sorry, I still don&#8217;t know how to invoke the code window. I don&#8217;t see # icon.
 
```

RESULTS.txt:
Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.

sda1: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Dell Utility: Fat16
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   /COMMAND.COM

sda2: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda2 and 
                       looks at sector 278432416 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   [COLOR="Red"]**/boot/grub/grub.cfg /bootmgr**[/COLOR] /Boot/BCD 
                       [COLOR="Red"][COLOR="Red"]**/boot/grub/core.img**[/COLOR][/COLOR]

sda3: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files/dirs:   

sda4: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

sda6: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 10.04.1 LTS
    Boot files/dirs:   /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda7: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1                  63        80,324        80,262  de Dell Utility
/dev/sda2    *         81,920    30,801,919    30,720,000   7 HPFS/NTFS
/dev/sda3          30,801,920   211,029,839   180,227,920   7 HPFS/NTFS
/dev/sda4         211,045,966   625,141,759   414,095,794   5 Extended
/dev/sda5         211,045,968   416,112,979   205,067,012   7 HPFS/NTFS
/dev/sda6         416,114,688   616,554,495   200,439,808  83 Linux
/dev/sda7         616,556,544   625,141,759     8,585,216  82 Linux swap / Solaris

```

---

### Post by drs305 on 2010-09-21
Forum member *meierfra* is the one who created the current version of the boot info script. It is a great contribution to the Ubuntu community.

When you start a new post, just above the first line you type should be a menubar starting on the left with Font selections and on the second row a **B** (for bold). Toward the far right of the second line should be the **#** icon. Clicking it generates the code tags. If you don't see the menu, you can add them manually by typing [noparse]```
 at the start and 
```[/noparse] at the end of the section you want within the window.

For the important matter of restoring W7, I'll have to defer to Windows users. I can tell you how to overwrite the current boot info but not how to restore Windows. (Well, I might be able to but I would be copying other threads without any direct knowledge.) The good news is that there are plenty of people who can.

The following link may help:
[How to restore the Ubuntu/XP/Vista/7 bootloader]("http://ubuntuforums.org/showthread.php?t=1014708")

---

### Post by moviglez on 2010-10-25
Grub rescue>- Is a curious error when install ubuntu 10.10.

It solved when the ubuntu cdlive version is update. 

Start with CdLive/UsbLive select option to try ubuntu. 
Open Terminal and update de system.

# apt-get update
# apt-get upgrade

And install all updates.

When finish, click icon "Install Ubuntu 10.10" and install ubuntu 10.10 to 100%. After reboot and the Grub works fine.

---

### Post by ashetz on 2011-07-20
Ei... I did your instructions and it shows that the installation was completed... but when i reboot my system it reveals a black screen:

GNU GRUB version 1.98+20100804-5ubuntu3

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

I need to fix this coz' I can't boot to windows 7:((

Hope you Understand..

---

### Post by drs305 on 2011-07-20
> **ashetz said:**
> Ei... I did your instructions and it shows that the installation was completed... but when i reboot my system it reveals a black screen:

GNU GRUB version 1.98+20100804-5ubuntu3

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or file completions.

I need to fix this coz' I can't boot to windows 7:((

Hope you Understand..

ashetz,

Welcome to the Ubuntu forums. :-)

It would be best to start your own thread. In it please post the contents of the RESULTS.txt file generated by running the boot info script from the LiveCD. The link for the script is:
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

---

### Post by KMPSJHS on 2012-09-07
Insert the ubuntu CD.select reinstall option.....Enjoy your existing operating system.

---

