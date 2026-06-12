---
title: "Is it possible to boot Ubuntu from Windows boot menu?"
date: 2006-07-08
forum: Desktop Environments
---

### Post by bartbes on 2006-07-08
Not that I like Windows, not at all. But GRUB takes a long time to start, about 5 mins. And LILO crashes.. so I can't boot in a time less than 5 mins. :-|

---

### Post by Rackerz on 2006-07-08
It's very stange that GRUB should take that long, have you tried reinstalling it? 

And Windows boot menu wont recognise Linux so I don't think their is a way to boot it from there.

---

### Post by bartbes on 2006-07-08
I've tried reinstalling LILO (as mentioned above) and a lot more, but it won't get faster... I'm getting the 6.06 LTS install and live in a few weeks, I hope that that GRUB version makes my booting faster:(

EDIT:
My menu.lst:
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
default saved

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
# kopt=root=/dev/hdb3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,2)

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

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-25-386
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hdb3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-25-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.15-25-386 root=/dev/hdb3 ro single
initrd		/boot/initrd.img-2.6.15-25-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb3 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hdb3 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, kernel 2.6.12-10-386
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdb3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hdb3 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd1,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hdb3 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd1,2)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1


```
BTW 2.6.12-10-386 is the kernel I'm working with (newer says something about my hard disk & BIOS)

---

### Post by jgcamp99 on 2006-07-08
Please provide the specs of your computer please, it shouldn't take 5 minutes to get to the Grub screen on anything. Grub to me is little more than a DOS like menu, very similar in appearance to the Bios screen(s) that come up every bootup. And Grub pulls up virtually immediately after the bios does it's thing.

---

### Post by bartbes on 2006-07-08
Well I have one 20GB disk as primary master with one partition (NTFS) that boots Win XP Home.
And a 250GB disk primary slave, with 4 partitions (1 NTFS, 1 FAT32, 1 EXT3, 1 SWAP) don't know why it says swap is hdb6 maybe empty space..
The 2nd disc isn't correctly supported by my BIOS (which the newer kernels say), but the long boot time was there already before the 2nd hard disk..

It's a Pentium III 733 MHZ, 512 MB RAM. And AFAIK nothing else can have an influence

---

### Post by tmahmood on 2006-07-08
Do you have any kind of USB devices connected? GRUB used to take a  lot of time in my system with a USB drive connected.

---

### Post by bartbes on 2006-07-08
Eeh..
My scanner - power plug not connected
My printer - most of the times off
My joystick - a wireless receiver
An USB hub - my scanner and my joystick are connected to it

and that's it, maybe it has to do something with the scanner, but this problem is there since I've installed Ubuntu (about 1,5 year ago) and as far as I remember I had an SCSI scanner back then, the printer connected to that. No hub, no joystick..

Maybe you want to know what's in my pc:
network card - in from the start
PCTV card - in from the start
sound card - in from the start
video card - later added (but I did have one before :p )

---

### Post by bartbes on 2006-07-08
Still no answer?

---

### Post by Malac on 2006-07-08
The way I did it was to install XP onto the first partition.
Then install Ubuntu onto the second partition.
Then altered XP boot menu.
To do this I did the following:
You will need a bootable MS-DOS disk with a copy of fdisk.exe on it.[LIST=1]
[*]Choose to install Ubuntu on the second, unused partition (aka D)
[*] When asked, choose GRUB as the boot loader
[*] Install GRUB on the first sector of the /boot partition e..g. /dev/hda2.
      *Important: If you tell it to install on the drive's master boot record (MBR) you wipe out Windows XP's boot selector. Not what you want.*
[*]Make sure this partition (/dev/hda2) is active i.e. bootable
[*]Reboot, it should go into Ubuntu
[*] Login and get to a shell
[*] Use *df* to check which filesystem device holds /boot (e.g. /dev/hda2)
[*] Insert the DOS floppy disk it should be mounted automatically but if not  mount it. (*sudo mount -t msdos /dev/fd0 /media/floppy*)
[*]Substituting your /boot device, enter:
      dd if=/dev/hda2 of=/mnt/floppy/bootsect.ubu bs=512 count=1
[*]Reboot off the floppy
[*]You will need to set the first partition active but this can be done with fdisk.
[*]Remove floppy and Reboot.
[*]**Set up the Windows boot menu**
[*] Boot into Windows XP if you're not already there
[*] Insert the DOS floppy disk
[*] Copy the BOOTSECT.UBU file from A:\ to C:\
[*] Open the System Properties window
[*] Click the Advanced tab
[*] Under *Startup and Recovery*, click Settings
[*] Click Edit to open the boot.ini file in Notepad
[*] Add this line to the end of the file and save:
      C:\BOOTSECT.UBU="Ubuntu"
[*] Close the Startup and Recovery settings, open it again, and Ubuntu should now appear in the *Default operating system* drop-down menu.
[*] Reboot and test it out[/LIST]Hope this Works for you.
If not let me know.

---

### Post by bartbes on 2006-07-09
What do you mean with > bootable DOS diskjust a normal floppy disk, or a windows/dos boot floppy?

And if I understand you ok I first have to boot win cdrom and do 'fixmbr'?

---

### Post by RawMustard on 2006-07-09
Just a normal floppy will do!
[Here's link on how to do it]("http://www.tprthai.net/bootmgr.htm")

---

### Post by bartbes on 2006-07-09
At that site I've found the reason why my new kernels can't boot.. because they are above 1024 cylinders (the error was something about too much cylinders)

---

### Post by krazykirk on 2006-07-09
hmm.. on that "Grub taking 5 mins to load" problem, i think the usb hub might be the problem.. on my dad's computer it stuffed his booting of his computer, so what you could try is just unpluging the hub then plugging it back in once you're past grub

---

### Post by ShiningHolden on 2006-07-09
Is it the GRUB menu taking the long time to load, or Ubuntu itself?

I could see ubuntu taking a while to load becuase upon kernel load, it probes for all USB deivces it when my iPod is connected it goes on and on about
```

usb: already loaded

```

I couldnt see how GRUB could take that long due to USB devices. I would think GRUB scans for it's entires on the defined devices, and, you get your output... 

Just hit me, scans USB for external drives with an OS?

Is it literally 5 minutes? Like, go get some Cola and Chips, 5 minutes? Or, just to slow?

I can't tell you to not use USB devices.

Make sure you have GRUB 0.97 installed, and not GRUB 2... I read, GRUB 2 is in development.

Try (re)installing GRUB 0.97.

```

System > Administartion > Synaptic Package Manager > Find GRUB > Verify GRUB2 is uninstalled > Right Click GRUB and check Reinstall

```

Hope this helps.

---

### Post by bartbes on 2006-07-10
[quote=bartbes]I had an SCSI scanner back then, the printer connected to that. **No hub**, no joystick..[/quote]

It doesn't take exactly 5 mins, but at least 3. And I have the GRUB from the install cd, tried to reinstall dozens of times. And BTW I've tried what Malac and RawMustard said, which got me in the position of not being able to boot linux again. Whilst I was busy with reinstalling grub, I've created an /boot partition (hdb7), I've put the new 2.6.15 kernels on that, and now they boot!  So at leat I've got my internet connection back online.

But still slow..
Does anyone knows why on my HDD I see:
Grub Loading Stage1.5
and on an floppy with GRUB (installed from install cd too):
Grub Loading Stage2

(Takes the same time)

And I know how fast it should boot (I've got some virtual machines with linux)

---

