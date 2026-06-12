---
title: "Help"
date: 2009-03-15
forum: General Help
---

### Post by dil3ma on 2009-03-15
Hey guys, I had Windows XP installed on one hard drive and then I installed Ubuntu on the other hard drive (I have 3 hard drives) and after installing ubuntu when it goes to boot up it boots up XP and not ubuntu, just wondering is there a way I can choose between the two OS and pick which one I want to boot from?
I went into my BIOS and had a look around in there and changed the boot sequence but I haven't had any luck, just wondering if there is something that I am doing wrong/have missed?
Thanks in advance.

---

### Post by kestrel1 on 2009-03-15
You probably have grub on the MBR of your Ubuntu drive, but you want it on the Windows Drive. Try this from a terminal: ```
sudo grub
root (hd0,1)
setup (hd0)
quit
```

Edit: Just remembered you cant get to Ubuntu. Use the Live CD.

---

### Post by vandorjw on 2009-03-15
I don't think that there is a need for that if you let just did a default installation without anything fancy. Grub is probably already installed, but on the other hard drive.

Go into BIO, and whatever hard drive you are booting from now, change it to your other one.
You will likely (hopefully) get a boot screen (also known as grub) from which you can select the OS of choice.

Cheers - CC7

---

### Post by hyper_ch on 2009-03-15
It is advised to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;)

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

See the forums policy, especially section II.2: [http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)

Also, when you are asked to post output from (config) files or from a command, use [noparse]```

```[/noparse] brackets around (each) output. That makes it also easier to read.

---

### Post by dil3ma on 2009-03-16
Okay hyper_ch, my bad, **** happens.
Turns out I got into grub and was able to use Ubuntu, fiddled with a few things, got dual monitors working and my graphcis card driver installed. I'm a noob with Linux so it took me a while. But I am having a few other  problems, one of them being when I go into grub and try to load Windows XP, it just says "Loading" or something similar to that and it just says that it's loading and doesn't do anything, I have left it for a long amount of time and still nothing. So now my problem is not being able to get into my Windows XP OS but I can get into Ubuntu :[
 the other problem I have is that I do not get any sound playing through my speakers, I have an inbuilt soundcard and my mother board is a gigabyte nforce 4 sli series (k8 triton series) I don't know if that helps, but yeah, I'd like to be able to accesss XP if possible and have sound when using Ubuntu. Again thank you in advance and if I haven't asked the question properly, don't flame me OK :]

---

### Post by kestrel1 on 2009-03-16
Can you post your grub menu. To do this type the following in a terminal:```
gedit /boot/grub/menu.lst
```
& can you post the output from the following:```
lspci
```

---

### Post by dil3ma on 2009-03-16
> **kestrel1 said:**
> Can you post your grub menu. To do this type the following in a terminal:```
gedit /boot/grub/menu.lst
```
& can you post the output from the following:```
lspci
```

I hope this is what you were asking me to do, again I apologise if I went wrong.
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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=f367888b-8c75-4c31-a641-54041ccc4336 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f367888b-8c75-4c31-a641-54041ccc4336

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

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		f367888b-8c75-4c31-a641-54041ccc4336
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=f367888b-8c75-4c31-a641-54041ccc4336 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		f367888b-8c75-4c31-a641-54041ccc4336
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=f367888b-8c75-4c31-a641-54041ccc4336 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f367888b-8c75-4c31-a641-54041ccc4336
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f367888b-8c75-4c31-a641-54041ccc4336 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f367888b-8c75-4c31-a641-54041ccc4336
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f367888b-8c75-4c31-a641-54041ccc4336 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f367888b-8c75-4c31-a641-54041ccc4336
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd1,0)
savedefault
makeactive
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1

```

---

### Post by kestrel1 on 2009-03-16
Could be wrong, but if you had XP already installed it would have been on hd0. I would suggest that you change the XP part of the grub menu to look like this:```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
To change the menu.lst do the following: ```
sudo gedit /boot/grub/menu.lst
```
& copy the above over the existing XP menu entry.
If you post the output from ```
lspci
``` We can have a look at the sound issue.

---

### Post by dil3ma on 2009-03-16
> **kestrel1 said:**
> Could be wrong, but if you had XP already installed it would have been on hd0. I would suggest that you change the XP part of the grub menu to look like this:```
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```
To change the menu.lst do the following: ```
sudo gedit /boot/grub/menu.lst
```
& copy the above over the existing XP menu entry.
If you post the output from [codelspci[/code] We can have a look at the sound issue.

Hey mate, I did the first part, but with the last part I'm a little stuck.
I press alt+f2 to get into the run application and type lspci but when I do that it doesn't end up showing me anything, I miss something again? Thank you.

---

### Post by kestrel1 on 2009-03-16
> **dil3ma said:**
> Hey mate, I did the first part, but with the last part I'm a little stuck.
I press alt+f2 to get into the run application and type lspci but when I do that it doesn't end up showing me anything, I miss something again? Thank you.
You need to open up the terminal Applications -> Accesories -> Terminal
& type ```
lspci
```
You should then get the result.
Have you restarted the machine to see if you can get in to Windows since changing Grub.

---

### Post by dil3ma on 2009-03-17
> **kestrel1 said:**
> You need to open up the terminal Applications -> Accesories -> Terminal
& type ```
lspci
```
You should then get the result.
Have you restarted the machine to see if you can get in to Windows since changing Grub.

Hey, I tried getting into windows, but now I get this:
"Starting up...
NTLDR is missing
Press CRTL+ALT+DEL to restart"

Okay, so I done the command you asked me to:
```
dilema@dilema:~$ lspci
00:00.0 Memory controller: nVidia Corporation CK804 Memory Controller (rev a3)
00:01.0 ISA bridge: nVidia Corporation CK804 ISA Bridge (rev a3)
00:01.1 SMBus: nVidia Corporation CK804 SMBus (rev a2)
00:02.0 USB Controller: nVidia Corporation CK804 USB Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation CK804 USB Controller (rev a3)
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation CK804 IDE (rev f2)
00:07.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:08.0 IDE interface: nVidia Corporation CK804 Serial ATA Controller (rev f3)
00:09.0 PCI bridge: nVidia Corporation CK804 PCI Bridge (rev a2)
00:0a.0 Bridge: nVidia Corporation CK804 Ethernet Controller (rev a3)
00:0b.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0c.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0d.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:0e.0 PCI bridge: nVidia Corporation CK804 PCIE Bridge (rev a3)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:07.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
01:08.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:08.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 62)
01:08.2 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 65)
01:0a.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)
05:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1)

```

p.s. I have 3 sata hard drives in my computer, one's 160 gig (used for storing movies, music, games, php codes, etc) and a 80 gig hard drive (ubuntu installed on it) and the other is 250 gig (windows xp installed) - don't know if that helps but yeah, any other ideas you can think of to help me access windows xp again? because I use xp for gaming, although I'm going to use ubuntu for everything else because it's ******* awesome. Thank you again for the help, much appreciated!

---

### Post by kestrel1 on 2009-03-17
The sound driver looks like it is installed. Have you checked that nothing is muted?
Do you know which hard drive Windows is installed on. I know you say it is the 250gb drive, but is this hd0, hd1?

---

### Post by dil3ma on 2009-03-17
> **kestrel1 said:**
> The sound driver looks like it is installed. Have you checked that nothing is muted?
Do you know which hard drive Windows is installed on. I know you say it is the 250gb drive, but is this hd0, hd1?

hey dude, turns out I have on board sound and I noticed that I ALSO have another sound card pluged in >.> completley forgot I put it in there ha! So I plugged my shiet into there and I now have sound, but only on two of my speakers (and the sub), I have 5 speakers and 1 sub.

I can open up my pc and see which sata port the 250 gig hard drive is plugged into, does that help? because I'm fair sure I installed the 250 gig hard drive last. I'll check and repost, peace out.

---

### Post by kestrel1 on 2009-03-17
I normally use gparted to check on the drives.
If you don't have it installed use```
sudo apt-get install gparted
```
It should then appear under System -> Administration -> Partition Editor
You can select each drive & see what file system it is using & how much space is on each drive. As long as you change nothing you will be fine. You should be able to see which drive your 250gb is.

---

### Post by dil3ma on 2009-03-17
> **kestrel1 said:**
> I normally use gparted to check on the drives.
If you don't have it installed use```
sudo apt-get install gparted
```
It should then appear under System -> Administration -> Partition Editor
You can select each drive & see what file system it is using & how much space is on each drive. As long as you change nothing you will be fine. You should be able to see which drive your 250gb is.

when I go to applications/accessories/terminal and type that line of code I get:
```
dilema@dilema:~$ sudo apt-get install gparted
[sudo] password for dilema: 
```
what should I try now? should I try search for gparted in synaptic package manager and install it through there? would that work? man I really hate doing all this to you lol
but yeah, tired of windows and only want to use it for gaming, eventually i'll learn enough to be able to do all this stuff on my own and help others starting out like me

---

### Post by dil3ma on 2009-03-17
hey, got gparted installed
the 250 gig is using ntfs file system
flags = boot
80 gig flags = boot
hmm
anything you want me to do now that I have gparted installed?

---

### Post by Dr.Suave on 2009-03-17
All you have to do there is type in your user password

EDIT: I see you beat me to it

---

### Post by kestrel1 on 2009-03-17
> **dil3ma said:**
> hey, got gparted installed
the 250 gig is using ntfs file system
flags = boot
80 gig flags = boot
hmm
anything you want me to do now that I have gparted installed?

Now you have gparted installed , if you can open it & on the right you will see a drop down list for your drives. I normally starts off at the first drive. What is the mount point for your XP disk. It should be something like /dev/sda. It tells you in the list.

---

### Post by dil3ma on 2009-03-17
> **kestrel1 said:**
> Now you have gparted installed , if you can open it & on the right you will see a drop down list for your drives. I normally starts off at the first drive. What is the mount point for your XP disk. It should be something like /dev/sda. It tells you in the list.

250 gig = dev/sdb

---

### Post by kestrel1 on 2009-03-17
In your grub menu.lst file change the following line under your XP heading
```
root		(hd0,0)
```
to this```
root		(hd1,0)
```

---

### Post by jwbrase on 2009-03-17
Actually, you can't just do that. You have to insert:

```
map (hd0) (hd1)
map (hd1) (hd0)
```

Before:

```
root (hd1,1)
```

Windows refuses to boot off of anything but hd0, so you have to configure Grub to switch things around so that hd0 becomes hd1 and vice versa. (Note that the sdX numbers do not change, only the hdX numbers).

hd0 starts out as whatever hard drive has been set up in the bios to boot first.

I learned all this a while ago when I migrated Wubi to my external drive.

---

### Post by kestrel1 on 2009-03-17
> **jwbrase said:**
> Actually, you can't just do that. You have to insert:

```
map (hd0) (hd1)
map (hd1) (hd0)
```

Before:

```
root (hd1,1)
```

Windows refuses to boot off of anything but hd0, so you have to configure Grub to switch things around so that hd0 becomes hd1 and vice versa. (Note that the sdX numbers do not change, only the hdX numbers).

hd0 starts out as whatever hard drive has been set up in the bios to boot first.

I learned all this a while ago when I migrated Wubi to my external drive.

oops, sorry forgot about remapping the drives.

---

### Post by dil3ma on 2009-03-17
> **jwbrase said:**
> Actually, you can't just do that. You have to insert:

```
map (hd0) (hd1)
map (hd1) (hd0)
```

Before:

```
root (hd1,1)
```

Windows refuses to boot off of anything but hd0, so you have to configure Grub to switch things around so that hd0 becomes hd1 and vice versa. (Note that the sdX numbers do not change, only the hdX numbers).

hd0 starts out as whatever hard drive has been set up in the bios to boot first.

I learned all this a while ago when I migrated Wubi to my external drive.

you said to insert before root(hd1,1)
but in my file it says
root (hd0,0)
but i'll insert that code above that line anyway and see what happens :]

---

### Post by dil3ma on 2009-03-17
> **dil3ma said:**
> you said to insert before root(hd1,1)
but in my file it says
root (hd0,0)
but i'll insert that code above that line anyway and see what happens :]
it says i don't have the permissions to save the file :S i'll keep messing with it and see if I can get it to save
//edit got it to save, i'll restart and see what happens, thanks

---

### Post by dil3ma on 2009-03-17
Wooo! It worked! Thank you so much for the help guys, I can now access windows xp to play games, but I'm going to use ubuntu as my primary OS because I think it shits all over windows and I've only been using ubuntu for what, 2 or 3 days now!
Plenty more questions to come lol :]

---

### Post by Peasantoid on 2009-03-17
> **dil3ma said:**
> it shits all over windows
Strange, you'd think Ubuntu'd be toilet-trained by now. ;)

---

### Post by jwbrase on 2009-03-17
> **dil3ma said:**
> you said to insert before root(hd1,1)
but in my file it says
root (hd0,0)
but i'll insert that code above that line anyway and see what happens :]

Wait... Now *I'm* confused. You've got it working, so don't change anything, but I'm not quite sure how it happened...

kestrel1 told you to change it from (hd0,0) to (hd1,0). That wouldn't work because it didn't have the mapping commands.

I *meant* to say you needed to make his changes and then add the mapping commands before (hd1,0). I ended up saying (hd1,1), which is from my setup, instead. That wouldn't work because the drive number was right but the partition number wasn't.

What I gather you did was to insert the mapping commands before (hd0,0) without changing it to (hd1,0). That shouldn't have worked on account of the drive number being wrong, but it seems it did anyways. :confused:

What did that line end up looking like in the end?

---

### Post by kestrel1 on 2009-03-18
If you could post your menu.lst, for reference & we can see what did actually work.```
gedit /boot/grub/menu.lst
```

---

### Post by dil3ma on 2009-03-18
> **kestrel1 said:**
> If you could post your menu.lst, for reference & we can see what did actually work.```
gedit /boot/grub/menu.lst
```

this is what I have:
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
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
# kopt=root=UUID=f367888b-8c75-4c31-a641-54041ccc4336 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=f367888b-8c75-4c31-a641-54041ccc4336

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

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		f367888b-8c75-4c31-a641-54041ccc4336
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=f367888b-8c75-4c31-a641-54041ccc4336 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		f367888b-8c75-4c31-a641-54041ccc4336
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=f367888b-8c75-4c31-a641-54041ccc4336 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f367888b-8c75-4c31-a641-54041ccc4336
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f367888b-8c75-4c31-a641-54041ccc4336 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f367888b-8c75-4c31-a641-54041ccc4336
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f367888b-8c75-4c31-a641-54041ccc4336 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		f367888b-8c75-4c31-a641-54041ccc4336
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
map (hd0) (hd1)
map (hd1) (hd0)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

---

### Post by kestrel1 on 2009-03-19
If your system is currently working OK in Ubuntu you could get rid of the older kernel version that is in your grub menu.

---

### Post by dil3ma on 2009-03-19
> **kestrel1 said:**
> If your system is currently working OK in Ubuntu you could get rid of the older kernel version that is in your grub menu.

yeah they're both working fine, so what part do I delete?
thank you

---

### Post by kestrel1 on 2009-03-19
> **dil3ma said:**
> yeah they're both working fine, so what part do I delete?
thank you
open up a terminal & type```
sudo gedit /boot/grub/menu.lst
```
Scroll down until you get to this part> title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		f367888b-8c75-4c31-a641-54041ccc4336
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f367888b-8c75-4c31-a641-54041ccc4336 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		f367888b-8c75-4c31-a641-54041ccc4336
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=f367888b-8c75-4c31-a641-54041ccc4336 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic
You can either delete the lines or comment them out like this```
##title		Ubuntu 8.10, kernel 2.6.27-7-generic
##uuid		f367888b-8c75-4c31-a641-54041ccc4336
##kernel		/boot/vmlinuz-2.6.27-7-generic ##root=UUID=f367888b-8c75-4c31-a641-54041ccc4336 ro quiet splash 
##initrd		/boot/initrd.img-2.6.27-7-generic
##quiet

##title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
##uuid		f367888b-8c75-4c31-a641-54041ccc4336
##kernel		/boot/vmlinuz-2.6.27-7-generic ##root=UUID=f367888b-8c75-4c31-a641-54041ccc4336 ro  single
##initrd		/boot/initrd.img-2.6.27-7-generic
```
Just make sure that it is the correct lines you are getting rid of, they must have the kernel 2.6.27-7 in the section.

---

