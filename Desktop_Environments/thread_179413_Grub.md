---
title: "Grub"
date: 2006-05-19
forum: Desktop Environments
---

### Post by i++ on 2006-05-19
Hi, i've read lots of forums about GRUB but can't find anything to solve this. I have 3 Hard drives, first one with windows xp on, 2nd one with Ubuntu install, and 3rd with fedora 5, just been installed. However, GRUB does not show Fedora, so i dont know how to boot it, any help?

Thanks :) -  a learning linux user...

how can i edit my GRUB so that i can boot off hdc to load Fedora?

---

### Post by tonyr on 2006-05-19
What does your GRUB menu.lst look like right now?
Are you using a mix of SATA and IDE drives?

---

### Post by Herman on 2006-05-19
> What does your GRUB menu.lst look like right now? Yes, can you please post it here, especially the bottom of it where the operating system entires to be booted are. Also, can you please post the output from ```
sudo fdisk -lu
``` thanks. :D Herman

---

### Post by i++ on 2006-05-19
Firstly, thanks for the quick replies :) output from fdisk is...

dave@davepc:~$ sudo fdisk -lu

Disk /dev/hda: 163.9 GB, 163928604672 bytes
240 heads, 63 sectors/track, 21175 cylinders, total 320173056 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *          63   320165999   160082968+   7  HPFS/NTFS

Disk /dev/hdb: 10.2 GB, 10242892800 bytes
255 heads, 63 sectors/track, 1245 cylinders, total 20005650 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *          63    19117349     9558643+  83  Linux
/dev/hdb2        19117350    20000924      441787+   f  W95 Ext'd (LBA)
/dev/hdb5        19117413    20000924      441756   82  Linux swap / Solaris

Disk /dev/hdd: 61.4 GB, 61492838400 bytes
255 heads, 63 sectors/track, 7476 cylinders, total 120103200 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdd1        42106428   120101939    38997756   17  Hidden HPFS/NTFS
/dev/hdd2   *          63      208844      104391   83  Linux
/dev/hdd3          208845    42106364    20948760   8e  Linux LVM

Partition table entries are not in disk order

and menu.lst looks like...

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
default		X_sequence

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-686 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-686
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-686 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.12-10-686
boot

title		Ubuntu, kernel 2.6.12-9-686 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-9-686 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-686
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-686 (recovery mode)
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.12-9-686 root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.12-9-686
boot

title		Ubuntu, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdd1
title		Microsoft Windows XP Professional
root		(hd2,0)
savedefault
makeactive
map		(hd0) (hd2)
map		(hd2) (hd0)
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1


any idea's? any thoughts at all would be much appreciated! only using IDE drives, no SATA.

Thanks

p.s. the Windows XP Professional install stated to be on (hd2,0) doesnt exist anymore...

---

### Post by i++ on 2006-05-19
*not sure if it is hdc i want to boot fedora from ,but i need to edit my grub so that it shows Ubuntu, XP and Fedora, so i have a choice :)
thanks

i++

---

### Post by Herman on 2006-05-19
> Device..............Boot..............Start................End...............Blocks...............Id...............System
/dev/hdd1............................42106428.....120101939.....38997756.........17..........Hidden HPFS/NTFS......(Windows XP Pro2)
/dev/hdd2.........      *............................          63...........    208844.........     104391........    83.........     Linux...............                (Fedora Core 5  )
/dev/hdd3.............................             208845........42106364   .......20948760    ........8e...........     Linux LVM.........            (Fedora boot partition) Hi, i++, Dave, Fedora Core made a seperate boot partition on LVM. I don't know much about LVM or about Fedora, but you are not the first person to have Grub problems with combining Fedora and other Linux systems.
I am sending you back my guess as to approximately how to edit your menu.lst, but you will need to do some work yourself to finish the job. Here's my guessed menu.lst entries as much as I can attempt to do:
```
## ## End Default Options ##

title Ubuntu, kernel 2.6.12-10-686
root (hd1,0)
kernel /boot/vmlinuz-2.6.12-10-686 root=/dev/hdb1 ro quiet splash
initrd /boot/initrd.img-2.6.12-10-686
savedefault
boot

title Ubuntu, kernel 2.6.12-10-686 (recovery mode)
root (hd1,0)
kernel /boot/vmlinuz-2.6.12-10-686 root=/dev/hdb1 ro single
initrd /boot/initrd.img-2.6.12-10-686
boot

#title Ubuntu, kernel 2.6.12-9-686
#root (hd1,0)
#kernel /boot/vmlinuz-2.6.12-9-686 root=/dev/hdb1 ro quiet splash
#initrd /boot/initrd.img-2.6.12-9-686
#savedefault
#boot

#title Ubuntu, kernel 2.6.12-9-686 (recovery mode)
#root (hd1,0)
#kernel /boot/vmlinuz-2.6.12-9-686 root=/dev/hdb1 ro single
#initrd /boot/initrd.img-2.6.12-9-686
#boot

title Ubuntu, memtest86+
root (hd1,0)
kernel /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root

title Fedora Core 5, kernel x.x.xx-xxx-xxx
root (hd2,2)
kernel /boot/vmlinuz-x.x.xx-xx-xxx root=/dev/hdd2 
initrd /boot/initrd.img-x.xx.xx-xx-xxx
savedefault
boot

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdd1
title Microsoft Windows XP Professional
root (hd2,0)
savedefault
makeactive
map (hd0) (hd2)
map (hd2) (hd0)
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1
```You will notice that I commented out your extra entries for your old Ubuntu Kernel with hash marks #, so they won't show up in your Grub Menu. That's optional, you can do that if you want to.

The words following the commands 'title' are not too important, you can type anything there that you like. I suggested 'Fedora Core 5 there.

What you insert after the 'root' command in each grub entry is important. I am guessing it will be (hd2,2) but to make sure, I'll give you links later to show you how to use Grub's command Line and have Grub do the research for you.

Likewise, exactly what you type after the 'kernel' command, is critical, and needs to be discovered exactly with help from Grub's command line. The name of your kernel and the path to it is what is needed, (most likely in the seperate boot partition somewhere). Next,  then the location of your /sbin/init file is to be put after the 'root=' part, (most likely your FC5 root partition).

Your initrd command also needs to be followed with the exact details if it is necessary to use initrd to boot Fedora. I'm not certian, because I have no Fedora experience. 

All these things can easily be found out so you can delete everywhere that I have put x's an replace the x's with the exact real information.

Here is how to use Grub's Command Line to check and make sure my guesses were correct, and also find the information I cannot guess from here.
Grub's [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") , and [What You Absolutely Need to Know]("http://www.troubleshooters.com/linux/grub/grub.htm#_What_You_Absolutely_Need_to_Know") **[B][B], **[/B][/B]and   [Having Grub Do Your Research For You]("http://www.troubleshooters.com/linux/grub/grub.htm#_Having_Grub_Do_Your_Research_For_You")

Between those three links I hope you will be able to figure out how to boot Fedora from the Grub Command Line. Take notes, because you use the same information edit your menu,lst file with afterwards. The commands that go in your Menu.lst are exactly the same as the ones you use from the command line, Having them in menu.lst just makes them automatic. Well in menu.lst there is the additional line with 'title', which you don't have to use from the command line, and also the 'savedefault' command is an extra one.

I hope that all works out okay for you, good luck with it, and let me know if there is anything you'd like explained a little more. :D Regards, Herman

---

### Post by i++ on 2006-05-20
okay, first attempt didnt work!

grub> null (hd2,1)/vmlinuz-2.6.15-1.2054_FC5smp

thats what i get for hd2,1, although im pretty sure thats the swap partition? :S hd2,0 should be the fedora one, but i can't find anything on it. Is the above my fedora 5 kernel? or the same version as it?

grub> find /sbin/init
 (hd1,0)

grub> find /vmlinuz
 (hd1,0)

grub> find /boot/vmlinuz

Error 15: File not found


:( not sure what to do to find it, i created the partition using partition magic 8 in win xp, so that fedora (hd2,0), and the swap would be (hd2,1) and then (hd2,2) SHOULD be just an ntfs partition.

am I right in thining that i just need to find the path's for /boot/vmlinuz and for /boot/initrd.img-xx.xx.....? and i'd need the absolute file names too i'd imagine...

thanks again for all the help!


UPDATE -- [http://www.badlydeveloped.com/partitions.JPG](http://www.badlydeveloped.com/partitions.JPG) - thats what it looks like visually... not sure if this helps but it looks like my Fedora install didnt go as well as planned ... lol im going to format disc3 and try a fresh install. thanks so much for your help, you may see me back again shortly.... :$ 

Thanks again,

Dave

---

### Post by Irony on 2006-05-20
Its quite simple just edit your current grub list (don't over install it with Fedora's);

[PHP]# This entry added by me as an example
# installation on /dev/hda9
title		Fedora Core 4, hda9
root		(hd0,8)
kernel		/boot/vmlinuz-2.6.11-1.1369_FC4 root=/dev/hda9 ro quiet splash
initrd		/boot/initrd-2.6.11-1.1369_FC4.img
savedefault

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		XP Home SP2, hda1
root		(hd0,0)
savedefault
makeactive
chainloader	+1
[/PHP]
To find out what your kernel and initrd file versions are, simply mount your Fedora partition from Ubuntu and navigate your way to the /boot folder and look up the exact versions.

---

### Post by i++ on 2006-05-20
ahh didnt think of doing that! thanks will try it now!


UPDATE -- It worked! thanks! :)

---

