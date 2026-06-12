---
title: "Cannot Dual boot with windows 7"
date: 2009-05-06
forum: General Help
---

### Post by snorbens on 2009-05-06
Hi,
I have been running only Ubuntu for quite some time. But as I needed to update my bios through windows dos thought I would make a partition and install the Windows 7 RC.

The problem I have is that I cannot dual boot with Windows.

I tried using the boot loader disc and tried to chainlink Ubuntu and Windows and it comes up with an error 13..something about uncompatible language.

I can therefore only boot now with ubuntu. If I re-install Windows then I can only boot into Windows7. My preffered OS is of course Ubuntu but would like to be able to boot into Windows as well if only for a short time.

Any help please.

Thanks Snorbens

---

### Post by wolfestine on 2009-05-06
Setting up a dual boot depends on how you have your hard disk set up. So mentioning your partition types would help.

---

### Post by snorbens on 2009-05-06
> **wolfestine said:**
> Setting up a dual boot depends on how you have your hard disk set up. So mentioning your partition types would help.

Hi, 
My disk are sda1 ext3 174.6Gib   Ubuntu Jaunty
            sda2 ntfs  42.61Gib  Windows7
            sda3 ext3  10.01Gib  Backup Partition
            sda4 extended 5.39Gib
            sda5 linux swap 5.39Gib

Hope this helps

Cheers

---

### Post by 343GuiltySpark on 2009-05-06
Hi, I just made up this configuration for my pc. Mine is actually a littler more complicated but the problem is kinda the same though.

After a long experience in dual booting ubuntu and windows (xp, vista, and 7) I can tell you that the solution to every your problem is let grub does all the work.

First do a clean install of windows 7. 7 will put his bootloader on your disk deleting everything he finds. Nice. xD

After that, do a clean install of Ubuntu. Ubuntu is much smarter and polite than windows: he will automatically detect 7 (even if it still thinks it's vista, but works anyway) and add a boot entry to grub.

So all you need is simply to install 7 and then ubuntu.

P.S: you can also try to repair the windows installation from its disk (that should restore 7's bootloader) and then reinstall grub from ubuntu's live cd. This way you don't have to format anything. It would be cool but never worked for me :(

---

### Post by gamblor01 on 2009-05-06
When you install Windows it's overwriting the MBR with the NT bootloader (or whatever they call it now) instead of grub.  It looks like you installed Ubuntu first, so it never had the chance to update your menu.lst file automatically with an entry for Windows.  So you have to do it manually.  It looks like your Windows installation is on /dev/sda2  which is also known as hd(0,1) so do the following:

1. Open up your /boot/grub/menu.lst file with a text editor.  I prefer vim but not everyone knows how to use that, so let's just use gedit.  You will need root privileges so use sudo:

```

$ sudo gedit /boot/grub/menu.lst

```2. Now paste the following lines at the end of the file:

```

# This entry is for Windows on /dev/sda2
title        Microsoft Windows 7
root        (hd0,1)
savedefault
makeactive
chainloader    +1

```3. save and close the file

4. reboot and make sure it works

---

### Post by gamblor01 on 2009-05-06
I just noticed that someone else posted at the same time I did.  I certainly don't think that reinstalling everything in the reverse order is the best idea.  That's a TON of work.  You can just edit the menu.lst file manually and be done with it in 10 seconds.

Just FYI, if you ever get to the point where Windows trashes your MBR and overwrites grub, you can easily put grub back in the MBR using a live cd.  I posted some info in this thread:

[http://ubuntuforums.org/showthread.php?t=1150267](http://ubuntuforums.org/showthread.php?t=1150267)

---

### Post by snorbens on 2009-05-06
> **gamblor01 said:**
> When you install Windows it's overwriting the MBR with the NT bootloader (or whatever they call it now) instead of grub.  It looks like you installed Ubuntu first, so it never had the chance to update your menu.lst file automatically with an entry for Windows.  So you have to do it manually.  It looks like your Windows installation is on /dev/sda2  which is also known as hd(0,1) so do the following:

1. Open up your /boot/grub/menu.lst file with a text editor.  I prefer vim but not everyone knows how to use that, so let's just use gedit.  You will need root privileges so use sudo:

```

$ sudo gedit /boot/grub/menu.lst

```2. Now paste the following lines at the end of the file:

```

# This entry is for Windows on /dev/sda2
title        Microsoft Windows 7
root        (hd0,1)
savedefault
makeactive
chainloader    +1

```3. save and close the file

4. reboot and make sure it works

Hi,
Thanks very much...on first boot did not work...but then put the code at the end of Default Options and then re-booted.

Thought I had buggered it up again as it booted straight into windows7:P

But then re-booted and pressed esc for other options and was able to boot into Ubuntu.

Will just have to remember to go into other options and choose Ubuntu before I make my coffee:).

Once again thanks for the help.

Snorbens

---

### Post by gamblor01 on 2009-05-06
Cool, glad to help.  It sounds like you have your grub menu hidden though.  You can change this by editing menu.lst again and changing the hiddenmenu option.  Up at the top of the menu.lst file you should see some options like this:

```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**[COLOR=Red]default        0[/COLOR]**

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[COLOR=Red]**timeout        10**[/COLOR]

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR=Red]**#hiddenmenu**[/COLOR]

```
The comments should make things pretty clear, but it sounds like your default is set to your Windows 7 entry (which is why it boots into Windows unless you intervene), and you probably have hiddenmenu uncommented.  I would suggest you *at least* change the default to whatever entry is for Ubuntu.  In this way it will boot into Ubuntu by default and only boot into Windows if you press esc and select it explicitly.

However, if you want to *always* see all of the boot options, then just comment out the hiddenmenu line (by adding the # sign at the beginning of the line).

---

### Post by snorbens on 2009-05-06
> **gamblor01 said:**
> Cool, glad to help.  It sounds like you have your grub menu hidden though.  You can change this by editing menu.lst again and changing the hiddenmenu option.  Up at the top of the menu.lst file you should see some options like this:

```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
**[COLOR=Red]default        0[/COLOR]**

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
[COLOR=Red]**timeout        10**[/COLOR]

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
[COLOR=Red]**#hiddenmenu**[/COLOR]

```
The comments should make things pretty clear, but it sounds like your default is set to your Windows 7 entry (which is why it boots into Windows unless you intervene), and you probably have hiddenmenu uncommented.  I would suggest you *at least* change the default to whatever entry is for Ubuntu.  In this way it will boot into Ubuntu by default and only boot into Windows if you press esc and select it explicitly.

However, if you want to *always* see all of the boot options, then just comment out the hiddenmenu line (by adding the # sign at the beginning of the line).

Thanks once again for that.... At the moment I have commented out the hiddenmenu.

The default was 0 but as a newbie unsure what I should make the default as do not want to alter anything that may mess it up again.

Thanks

---

### Post by gamblor01 on 2009-05-06
default 0 just means that the first entry in your menu.lst file is going to be booted if you don't take any other action.  If you pasted in the entry for Windows at the end of menu.lst then it's really strange that it would be considered the first option.

> 
The default was 0 but as a newbie unsure what I should make the default as do not want to alter anything that may mess it up again.


Well, quite frankly the best way to learn how to do stuff in Linux is trial and error.  ;)

If you want to post your menu.lst I am willing to take a look and tell you what default should be set to in order to make Ubuntu be the "default" operating system.  Fortunately, you can be safely change default to other values and see what happens.  There is no possible way to "mess it up" to the point where you can't boot one OS or the other.  The only thing it will do is select one of the partitions by default -- meaning it will boot that partition if you don't press anything by the timeout value.  But since you should have about 10 seconds or so anyway, you have plenty of time to press up or down and select a different partition manually.

Every time you reboot now you should get the menu full of options and you can boot both now.  So if you're happy and just want to leave it alone now, I understand that as well.

---

### Post by snorbens on 2009-05-06
> **gamblor01 said:**
> default 0 just means that the first entry in your menu.lst file is going to be booted if you don't take any other action.  If you pasted in the entry for Windows at the end of menu.lst then it's really strange that it would be considered the first option.



Well, quite frankly the best way to learn how to do stuff in Linux is trial and error.  ;)

If you want to post your menu.lst I am willing to take a look and tell you what default should be set to in order to make Ubuntu be the "default" operating system.  Fortunately, you can be safely change default to other values and see what happens.  There is no possible way to "mess it up" to the point where you can't boot one OS or the other.  The only thing it will do is select one of the partitions by default -- meaning it will boot that partition if you don't press anything by the timeout value.  But since you should have about 10 seconds or so anyway, you have plenty of time to press up or down and select a different partition manually.

Every time you reboot now you should get the menu full of options and you can boot both now.  So if you're happy and just want to leave it alone now, I understand that as well.

Hi,
Thanks once again.
Yes I understand what you are saying....that is how I educated myself with that expensive OS but as I am about to get my bus pass I find it a slower experience at the moment.:(

Here is my grub menu list for your perusal and once again thanks.
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		5

 hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
## password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=cd95bc73-766f-41b0-bbee-84999da835a8 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=cd95bc73-766f-41b0-bbee-84999da835a8

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## specify if running in Xen domU or have grub detect automatically
## update-grub will ignore non-xen kernels when running in domU and vice versa
## e.g. indomU=detect
##      indomU=true
##      indomU=false
# indomU=detect

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false
# This entry is for Windows on /dev/sda2
title        Microsoft Windows 7
root        (hd0,1)
savedefault
makeactive
chainloader    +1
## ## End Default Options ##

title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		cd95bc73-766f-41b0-bbee-84999da835a8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=cd95bc73-766f-41b0-bbee-84999da835a8 ro quiet splash 
initrd		/boot/initrd.img-2.6.28-11-generic
quiet

title		Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid		cd95bc73-766f-41b0-bbee-84999da835a8
kernel		/boot/vmlinuz-2.6.28-11-generic root=UUID=cd95bc73-766f-41b0-bbee-84999da835a8 ro  single
initrd		/boot/initrd.img-2.6.28-11-generic

title		Ubuntu 9.04, memtest86+
uuid		cd95bc73-766f-41b0-bbee-84999da835a8
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST 
```

---

### Post by snorbens on 2009-05-06
Hi again,

Just realised why windows was booting first..

When I initially pasted the lines for Windows to appear in the grub at the end of the file and re-booted it did not appear so then I pasted it at the end of the default options, not realising that the menu was hidden.

I have now done just what you said in the first place and inserted the lines at the END of the file and now Ubuntu is the first boot.

Thanks once again.

---

### Post by gamblor01 on 2009-05-06
Yep I just noticed that when I looked at your menu.lst file.  Makes sense now.  Hooray!!  Everything works.  :)

---

