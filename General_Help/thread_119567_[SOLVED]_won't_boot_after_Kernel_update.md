---
title: "[SOLVED] won't boot after Kernel update"
date: 2006-01-19
forum: General Help
---

### Post by ubuntu27 on 2006-01-19
Hi guys and girls!

TOday (1/19/2006), I upgrade the kernel image [or was it Kernel package?] when I saw the "UPdate avaiable" icon.

After installing it, it told me to reboot, and so I did.

Now I cannot run ubuntu.

 This is what I get:

```
Booting 'Ubuntu, kernel 2.6.12-10-386 '

root (hd0,2)
  Filesystem type unknown, partition type 0x5
  Kernel /boot/vmlinuz -2.6.12-10-386 root=/dev/hda3 ro quiet splash

Error 17: Cannot mount selected partition

Press any key to continue....

```
Any help, any tip, anything will pe aperciated :)

Thank you in advance guys/girls

---

### Post by Qrk on 2006-01-19
Do the other kernels listed in Grub still boot?

---

### Post by ubuntu27 on 2006-01-19
[QUOTE=Qrk]Do the other kernels listed in Grub still boot?[/QUOTE]
NO, it dosn't. :(  None of the kernels will boot.

---

### Post by ubuntu27 on 2006-01-20
.... ***pomp*** 

I need thy help guys! :(

---

### Post by strazzere on 2006-01-20
None of your selections in GRUB work?

Do they all provide the same error of, "Error 17: Cannot mount selected partition"?

If so I think the update may have corrupted the partition... I'm no guru though - so I'm just taking a stab at it. Last time something that happened to me, lucky I had just installed and done updates, so I reinstalled the distro. Tried the updates again and it seems to work fine.

Hopefully someone else knows a better way than that though.

---

### Post by ubuntu27 on 2006-01-20
[QUOTE=strazzere]None of your selections in GRUB work?

Do they all provide the same error of, "Error 17: Cannot mount selected partition"?

If so I think the update may have corrupted the partition... I'm no guru though - so I'm just taking a stab at it. Last time something that happened to me, lucky I had just installed and done updates, so I reinstalled the distro. Tried the updates again and it seems to work fine.

Hopefully someone else knows a better way than that though.[/QUOTE]
Yeah, I guess the kernel upgrade has corrupted the partition.
I am hoping that there could be a solution to that problem since I have many files.

And, yeah, none of the kernels/Ubuntu works now.
I am currently using Windows :(

---

### Post by flosofl on 2006-01-20
Well, I'm thinking right now that your installation is dead.  Key point here:  Did/does the drive sound... unusual?  A lot of clicking or excessive whirring?  That would most likely be a harware failure.  Recoverable but it would require tools you most likely won't have at home (such as a hermetically sealed chamber to take apart the assembly).

If not, read on.  It may be just a bad chain or sectors in an inopportune spot.  Even if you suspect a hardware failure, you may as well try to recover (even though there is large chance you will not get anything)

Was this a single partition install or did you create different partitions for various mount points.  I'm thinking specifically of /var for server stuff and /home for your personal stuff.  With multiple partitions, you may have a slightly better chance to recover info uncorrupted if the problem(s) are restricted to the / partition.

Regardless, get a copy of [Knoppix STD]("http://www.knoppix-std.org/") - I use it in my job a lot and it has a ton of tools to recover data and info from drives.   Boot up STD and try to mount the drive - you may be able to get data and copy it to a USB attached device.  There is a ton of stuff on this CD, so take a look at the tools included and read the help files and on the internet about them.  Since you aren't worried about chain of custody like I would be, run fsck on your e3fs partitions to see if that helps.

If it's not an actual hardware failure such as a stepper motor issue, head crash, or the like, you should have a better than even chance of getting most of data back.

EDIT: Changed incorrect "STP" to correct "STD".  D'oh!

---

### Post by ubuntu27 on 2006-01-20
Thank you flosofl :)

I have four partitions,  NTFS, fat32, Ext2, Swap

I guy told me in the Ubuntu channel to change (hd0,0) to (hd0.2) by hitting "e" in the keuboard on the Grub menu. But, I saw that it was alread in (hd0,2) so I changed to (hd0,3) [Which I remember that my ubuntu partition is] and got the following:

```
    Booting Command-list
   root (hd0,3)
    Filesystem type is ext2fs, partition type 0x83
   Kernel /boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash
      [Linux-bzImage, setup=0x1x00, size=0x
  initrd /boot/initrd.img-2.6.12-10-3 0x124ce9]
      [Linux-initrd @ 0x1f2dc000, 0x50d02b bytes]
  Savedefault
  boot
  uncompressing Linux... Ok, booting the kernel.
  loading, please wait...
  fstype: short read
  usage: modprobe [-v] [-V] [-C config-file] [-n] [-i] [-q] [-o <modname>] <modname [parameters...]
  
  modprobe -r [-n] [-i] [-v] <modulename>...
  modprobe -l -t <dirname> [-a <modulename>...]

  mount:
  Cannot read /etc/fstab: No such file or directory
  mount: Mounting /root/dev on /dev/.static/dev failed: no such a file or directory
  
  Target filesystem dosn't have /sbin/init
```

anybody have an idea?

---

### Post by Limulus on 2006-01-20
Here's something that you can use to peek into your linux partition from Windows: [Explore2fs](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm) (its neat; I've used it before)

Do you see all your files still there?

Can you use Explore2fs to get a copy of /boot/grub/menu.lst and post a copy here?

---

### Post by ubuntu27 on 2006-01-21
[QUOTE=Limulus]Here's something that you can use to peek into your linux partition from Windows: [Explore2fs](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm) (its neat; I've used it before)

Do you see all your files still there?

Can you use Explore2fs to get a copy of /boot/grub/menu.lst and post a copy here?[/QUOTE]

Oh yes! I can Access my Linux partition with explore2fs!! yey! [that gives me hopes!]

Thank you Limulus :)

Here is the menu.lst:

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,2)

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

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Windows NT/2000/XP
root		(hd0,0)
savedefault
makeactive
chainloader	+1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Windows NT/2000/XP (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1


```

mmm... ***Thinking***

Ok, I don't if I am right, but, do I have to replace ALL (hd0,2) with (hd0,3) ?

What should I do now?

Thank you guys (in advance) :)

---

### Post by ubuntu27 on 2006-01-21
:cry:  Where are you guys?

---

### Post by ubuntu27 on 2006-01-21
****bump***

---

### Post by Limulus on 2006-01-21
[QUOTE=ubuntu27]Here is the menu.lst:

*snip*```

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot
```*snip*

mmm... ***Thinking***

Ok, I don't if I am right, but, do I have to replace ALL (hd0,2) with (hd0,3) ?

What should I do now?

Thank you guys (in advance) :)[/QUOTE]

Sorry to get you antsy; I wasn't able to get back to my computer until now :)

I'm thinking that what happened was that when you installed the upgrade, when the GRUB list was rewritten, there was a mistake somewhere.

So yes, try changing (hd0,2) to (hd0,3) (which is what I think you basically did before where it partially booted) but also try changing root=/dev/hda3 to root=/dev/hda4

---

### Post by Limulus on 2006-01-22
Happy news: while UF was down, I talked to him on IRC (#ubuntuforums) and that solved the problem :)

---

### Post by ubuntu27 on 2006-01-22
[QUOTE=Limulus]Happy news: while UF was down, I talked to him on IRC (#ubuntuforums) and that solved the problem :)[/QUOTE]


Thank you Limulus!! My 6th senses [joke] told me me that there is still hope :D

Yeah, and like he [Limulus] said, we "met" in the #ubuntuforums in freenode, and he rescued me :D

---

### Post by mishranurag on 2006-01-23
How do you get in IRC freenode?? I could not understand that system :)

Anurag

[quote=ubuntu27]Thank you Limulus!! My 6th senses [joke] was told me me that there is still hope :D

Yeah, and like he [Limulus] said, we "met" in the #ubuntuforums in freenode, and he recued me :D[/quote]

---

### Post by Whtbflo on 2006-01-23
Can you detail what you did to solve this?  I am having a similiar problem. After a  kernel upgrade, I cannot boot to any of the kernels listed in grub.  Mine hangs at "ok..booting the kernel"   though

---

### Post by lha on 2006-01-23
[QUOTE=ubuntu27]Thank you Limulus!! My 6th senses [joke] told me me that there is still hope :D

Yeah, and like he [Limulus] said, we "met" in the #ubuntuforums in freenode, and he recued me :D[/QUOTE]

Nice to hear your problem was solved. Did you fix also kopt and groot?

---

### Post by ubuntu27 on 2006-01-23
[QUOTE=mishranurag]How do you get in IRC freenode?? I could not understand that system :)

Anurag[/QUOTE]
In Ubuntu, go to Applications/Internet/X-Chat IRC



X-chat Server List will be open, write down your nick [any nick] and _select Ubuntu Servers_ and click on Connect. And you are good to go! You are now in #Ubuntu channel [Technical Support channel], and if you want to go to the #UbuntuForums channel [talking about anything...]  

Write:  /join #ubuntuforums

If you want to change your nick:   /nick 'insertname'


And, if you are NOT in ubuntu

Open Your IRC Chat Program. You can find OpenSource IRC for Windows here: [http://osswin.sourceforge.net/#irc](http://osswin.sourceforge.net/#irc)

And when you choose Servers, select "Freenode" or &#8220;Freenode.net&#8221; now after conecting to Freenode, you now have to jump in some channel. In our case Ubuntu channel, so  we type, " /join #ubuntu "  and voila! Now you are in [email]Ubuntu@freenode.net[/email]

---

### Post by Limulus on 2006-01-23
[QUOTE=mishranurag]How do you get in IRC freenode?? I could not understand that system :)[/QUOTE]
IRC = Internet Relay Chat; If you boot with the Live CD you can use the program  "XChat".  There are lots of IRC clients for lots of OSs; see Wikipedia's entry for more info: [http://en.wikipedia.org/wiki/Internet_Relay_Chat](http://en.wikipedia.org/wiki/Internet_Relay_Chat)

Once you get an IRC client running, you connect to the FreeNode network (irc.freenode.net) and then run a command like */join #ubuntuforums* to get connected to that 'channel'.

BTW, the whole reason we were on IRC was because Ubuntu Forums was down at the time ;)  So you can post here and that will work if you don't want to learn a new program.

---

### Post by Limulus on 2006-01-23
[QUOTE=lha]Nice to hear your problem was solved. Did you fix also kopt and groot?[/QUOTE]
*blink* I have no idea what this means :)  He was only having trouble booting because of an incorrect GRUB list...

---

### Post by ubuntu27 on 2006-01-23
[QUOTE=Whtbflo]Can you detail what you did to solve this?  I am having a similiar problem. After a  kernel upgrade, I cannot boot to any of the kernels listed in grub.  Mine hangs at "ok..booting the kernel"   though[/QUOTE]

ok. I will give the details.

I run Windows OS and downloaded [Explore2fs ](http://uranus.it.swin.edu.au/~jn/linux/explore2fs.htm)

And saw that I can access my ext3 [which some how became ext2!??] Ubuntu partition.  Which of course gave hope since plp told me that my partition was damaged and thus the only solution will be to format.


I booted the Ubuntu Breezy LIVE CD.

And run &#8220;Disks&#8221; from  System/Administration/Disks

There I/you could see all your partitions and your HD. 
I selected my HD [I only have 1], and in the &#8220;Partitions&#8221; tab I looked my Ubuntu partition, which in MY case it was on &#8220;Partition 4&#8221; 

And paying attention to the status, it says &#8220;Inaccesible&#8221; 

in the Access Path, I wrote: &#8220;/mnt&#8221; and Click Enable. And now I could access my Ubuntu partition.

Limulus told me to click &#8220;Browse&#8221; and so I did and opened my menu.lst which is located at /boot/grub/menu.lst 

And I had to change some values. In MY case  

(hd0,2) -------> (hd0.3)
root=/dev/hda3  ------->  root=/dev/hda4

Well, looks like the Kernel mistook where is My Linux partition. My Linux partition was on hda4.

And that's it! I rebooted, and Voila! I'm running Ubuntu again :D

---

### Post by Limulus on 2006-01-23
> **ubuntu27]my ext3 [which some how became ext2!??] Ubuntu partition.[/quote]
I was wondering about that said:**
> in the Access Path, I wrote: “/mnv” and Click Enable. And now I could access my Ubuntu partition.


That should read "/mnt" (as in "mount")... I don't know if other values will work or not ;)

---

### Post by Limulus on 2006-01-23
[QUOTE=Whtbflo]Can you detail what you did to solve this?  I am having a similiar problem. After a  kernel upgrade, I cannot boot to any of the kernels listed in grub.  Mine hangs at "ok..booting the kernel"   though[/QUOTE]

There's a good chance that your GRUB list is wrong in some way; try to use the methods ubuntu27 mentioned to get a copy and post it here.  Also, if you have some idea of what your partitions are (e.g. find out via the Live CD as ubuntu27 mentioned... oh and don't be surprised if you see three HDs listed in the Live CD Disks utility; two of those are virtual and one will be your real drive of approximately the correct size; e.g. for ubuntu27 his 120 GB drive was listed as ~112 GB)

---

### Post by Whtbflo on 2006-01-23
thanks for posting the details, but unfortunately my problem appears to be something different (IRQs appear to be broken, can't even boot a rescue cd)
back to the drawing board......

---

### Post by caneycreek on 2006-01-23
I'm having the same issue with kernel 2.6.15-13-amd64, with some differences:

[LIST]
[*]Selecting 13 results in "File not found"
[*]Selecting 12 boots normally
[*]There is no file system corruption
[/LIST]

Here is an edited menu.lst (I've left out recovery mode & memtest):

```
title		Ubuntu, kernel 2.6.15-13-amd64-generic 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-13-amd64-generic root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-13-amd64-generic
savedefault
boot

title		Ubuntu, kernel 2.6.15-12-amd64-generic 
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-12-amd64-generic root=/dev/hdd1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-12-amd64-generic
savedefault
boot
```

I've verified that all of these files exist. Any ideas?

---

### Post by Limulus on 2006-01-24
[QUOTE=Whtbflo]thanks for posting the details, but unfortunately my problem appears to be something different (IRQs appear to be broken, can't even boot a rescue cd) back to the drawing board......[/QUOTE]
Can you tell us a little about your system? (Is it dual/multiboot?  If so, do the other OS(s) boot? Can you boot from a Live CD?)

---

### Post by ubuntu27 on 2006-01-24
caneycreek. That dosn't seem like it is your COMPLETE menu.lst. 

Can you post it again?

---

### Post by ubuntu27 on 2006-01-24
[QUOTE=Limulus]I was wondering about that; when you partitioned your HD when you first setup Ubuntu, did you maybe by accident select ext2 instead of ext3?  If not, its a mystery to me! :-)
[/QUOTE]

Well, when I installed Ubuntu for the first time, it was ext3, I thnk it "bacame" ext2 after my first or second Kernel Upgrade.


You know....  I AM HAVING KERNEL-PHOBIA NOW. I will never ever upgrade the kernel !!  ><

---

### Post by Limulus on 2006-01-24
[QUOTE=caneycreek]I'm having the same issue with kernel 2.6.15-13-amd64, with some differences:

[LIST]
[*]Selecting 13 results in "File not found"
[*]Selecting 12 boots normally
[*]There is no file system corruption
[/LIST]
*snip*

I've verified that all of these files exist. Any ideas?[/QUOTE]

Um... kernel 2.6.15?  Breezy has version 2.6.12; according to packages.ubuntu.com 2.6.15 is in Dapper.  Dapper is currently *alpha* software (e.g. buggy).  Solution: use 2.6.15-12 (since it works :) and wait for 2.6.15-14 (which will likely be along shortly) to see if that works on your system and/or try reinstalling the 2.6.15-13 packages in Synaptic to see if that fixes the problem somewhere.

---

### Post by Limulus on 2006-01-24
[QUOTE=ubuntu27]caneycreek. That dosn't seem like it is your COMPLETE menu.lst. Can you post it again?[/QUOTE]
He really doesn't need to; basically all we needed to see was one or two entries (especially the main one), which he provided.

---

### Post by Limulus on 2006-01-24
[QUOTE=ubuntu27]Well, when I installed Ubuntu for the first time, it was ext3, I thnk it "bacame" ext3 after my first or second Kernel Upgrade. You know....  I AM HAVING KERNEL-PHOBIA NOW. I will never ever upgrade the kernel !! [/QUOTE]

Just to double check, when you go into System -> Administration -> Disks and click on the Ubuntu partition (hda4 for you), does it say "Extended 2" for "Filesystem"?

---

### Post by lha on 2006-01-24
[QUOTE=Limulus]*blink* I have no idea what this means :)  He was only having trouble booting because of an incorrect GRUB list...[/QUOTE]

Menu.lst has lines like this:
```
#kopt=root=/dev/hda1 ro
```
and
```
#groot=(hd0,0)
```
Whenever kernel is upgraded, update-grub is invoked and update-grub recreates all menu entries between
```
### BEGIN AUTOMAGIC KERNELS LIST
```
and
```
### END DEBIAN AUTOMAGIC KERNELS LIST
```
using kopt and groot to determine which partition is passed as an option to grub's root command and to kernel. Even though kopt and groot are commented out, they are still used in this way. So if devices in kopt and groot are not corrected, ubuntu27 will end up with this same problem when he/she upgrades kernel next time.

---

### Post by lha on 2006-01-24
[QUOTE=ubuntu27]Well, when I installed Ubuntu for the first time, it was ext3, I thnk it "bacame" ext3 after my first or second Kernel Upgrade.


You know....  I AM HAVING KERNEL-PHOBIA NOW. I will never ever upgrade the kernel !!  ><[/QUOTE]

Your partition probably hasn't changed into ext2. Try
```
mount
```
and find the line with your root device. It will say something like
```
/dev/hdaX on / type ext3 (rw)
```
That ext3 means it is mounted as ext3. If there is ext2, then something has happened. I haven't read much about filesystems, but something like "ext3=ext2+journalling" is quite close to the truth. Ext3 partitions can be mounted as ext2.

Please, don't have a kernel phobia, your problems were caused by two wrong settings in menu.lst. Those poor kernels had nothing to do with it... :)

---

### Post by Limulus on 2006-01-24
[QUOTE=lha]Menu.lst has lines like this:
```
#kopt=root=/dev/hda1 ro
```
and
```
#groot=(hd0,0)
```
Whenever kernel is upgraded, update-grub is invoked and update-grub recreates all menu entries between
```
### BEGIN AUTOMAGIC KERNELS LIST
```
and
```
### END DEBIAN AUTOMAGIC KERNELS LIST
```
using kopt and groot to determine which partition is passed as an option to grub's root command and to kernel. Even though kopt and groot are commented out, they are still used in this way. So if devices in kopt and groot are not corrected, ubuntu27 will end up with this same problem when he/she upgrades kernel next time.[/QUOTE]

I had no idea :)  I did mention to him that he should watch carefully in the future to make sure it put in the correct ones (and if not to manually correct them).  An automatic method would be great, so thanks for teaching me about those! :)

so for ubuntu27, he should change them from:

```

# kopt=root=/dev/hda3 ro
# groot=(hd0,2)

```

to:

```

# kopt=root=/dev/hda4 ro
# groot=(hd0,3)

```

---

### Post by Whtbflo on 2006-01-24
[QUOTE=Limulus]Can you tell us a little about your system? (Is it dual/multiboot?  If so, do the other OS(s) boot? Can you boot from a Live CD?)[/QUOTE]

it is a thinkpad A22, with only Breezy on it. I can't get the Live CD to boot, or system rescue CD (gentoo kernel 2.4).  Ubuntu (live and installed) hangs after the line;
 ACPI:PCI intyerupt 0000:00:03.1[a] ->Link[lNKC] -> GSI (level,low) ->IRQ11
System rescue provides this detail:
PCI:found IRQ 11 with 00:03.0 redundant entry in serial PCI_table

I have tried various boot arguments (noapic , ACPI=on, ACPI=noirq, etc) to no avial.  I have manually reset the IRQs for PCI to auto detect and various other values also to no avail.

---

### Post by caneycreek on 2006-01-24
[QUOTE=Limulus]Um... kernel 2.6.15?  Breezy has version 2.6.12; according to packages.ubuntu.com 2.6.15 is in Dapper.  Dapper is currently *alpha* software (e.g. buggy).  Solution: use 2.6.15-12 (since it works :) and wait for 2.6.15-14 (which will likely be along shortly) to see if that works on your system and/or try reinstalling the 2.6.15-13 packages in Synaptic to see if that fixes the problem somewhere.[/QUOTE]
Yes, I've tried that, and yes, it's Dapper. I just wondered if anyone' seen anything like this before when the menu.lst file was not broken but it still can't find the file. I suspect that the next upgrade will do the trick. Till then I'll post to the dapper dev forum. Thanks!

---

### Post by Limulus on 2006-01-24
> **Whtbflo]it is a thinkpad A22, with only Breezy on it. I can't get the Live CD to boot, or system rescue CD (gentoo kernel 2.4).  Ubuntu (live and installed) hangs after the line said:**
>  ->Link[lNKC] -> GSI (level,low) ->IRQ11
System rescue provides this detail:
PCI:found IRQ 11 with 00:03.0 redundant entry in serial PCI_table

I have tried various boot arguments (noapic , ACPI=on, ACPI=noirq, etc) to no avial.  I have manually reset the IRQs for PCI to auto detect and various other values also to no avail.
The fact that you can't boot from the Breezy Live CD (but that you previously had Breezy working on your system) is a bad sign; it *should* boot no problem.  Off the top of my head, it could be that the BIOS on your system is corrupted...  Maybe go to [IBM's tech site](http://www-307.ibm.com/pc/support/site.wss/document.do?lndocid=TPAD-MATRIX) and download the BIOS image and reinstall it on the computer.  That shouldn't hurt any local files...  If that doesn't work (or you don't want to mess with the BIOS), try posting a new thread in the [hardware section of the forum](http://ubuntuforums.org/forumdisplay.php?f=98) with a detailed post with all the info you've posted here...

---

### Post by Whtbflo on 2006-01-24
You were right about the BIOS. I updated and can now boot into the previous version of the kernel 2.6.12-9, but the new version 2.6.12-10 still won't boot.   I didn't consider that a kernel upgrade could corrupt the BIOS. Thanks for pointing me in the right direction

---

### Post by Limulus on 2006-01-24
[QUOTE=Whtbflo]You were right about the BIOS. I updated and can now boot into the previous version of the kernel 2.6.12-9, but the new version 2.6.12-10 still won't boot.   I didn't consider that a kernel upgrade could corrupt the BIOS. Thanks for pointing me in the right direction[/QUOTE]
You're welcome; glad my gut feeling on this was right... It might be that it was a coincidence that the BIOS failed right around when you upgraded (or maybe not... computers still have a little bit of [magic](http://www.catb.org/~esr/jargon/html/magic-story.html) left in them ;)  Regardless though, now that you can at least boot it with *something*, you're on the right track to figure out why that kernel won't boot on your system; have you tried all the things you tried before you reinstalled the BIOS? ("I have tried various boot arguments (noapic , ACPI=on, ACPI=noirq, etc) ")

---

### Post by Whtbflo on 2006-01-24
AAAARRRGH!!! in trying to get the new kernel to boot, it corrupted the BIOS again, but now the wonderful IBM util won't let me overwrite the BIOS because its the same level.  Off to search on how to force an update

---

### Post by Limulus on 2006-01-24
[QUOTE=Whtbflo]AAAARRRGH!!! in trying to get the new kernel to boot, it corrupted the BIOS again, but now the wonderful IBM util won't let me overwrite the BIOS because its the same level.  Off to search on how to force an update[/QUOTE]
This sounds bad; I think you should start a thread in the [hardware section of the forum](http://ubuntuforums.org/forumdisplay.php?f=98) and hopefully they can help you :(

---

### Post by ubuntu27 on 2006-01-25
> **Limulus]Just to double check, when you go into System -> Administration -> Disks and click on the Ubuntu partition (hda4 for you), does it say "Extended 2" for "Filesystem"?[/QUOTE]

It says &#8220 said:**
> I had no idea :)  I did mention to him that he should watch carefully in the future to make sure it put in the correct ones (and if not to manually correct them).  An automatic method would be great, so thanks for teaching me about those! :)

so for ubuntu27, he should change them from:

```

# kopt=root=/dev/hda3 ro
# groot=(hd0,2)

```

to:

```

# kopt=root=/dev/hda4 ro
# groot=(hd0,3)

```

Alright, I changed them. I am gonna give it another chante to the kernel upgrade.... >< :D

Thank you again Limulus. :)

[QUOTE=lha]Your partition probably hasn't changed into ext2. Try
```
mount
```
and find the line with your root device. It will say something like
```
/dev/hdaX on / type ext3 (rw)
```
That ext3 means it is mounted as ext3. If there is ext2, then something has happened. I haven't read much about filesystems, but something like "ext3=ext2+journalling" is quite close to the truth. Ext3 partitions can be mounted as ext2.

Please, don't have a kernel phobia, your problems were caused by two wrong settings in menu.lst. Those poor kernels had nothing to do with it... :)[/QUOTE]

Here is the result of "mount"

```
ubuntu27@heaven:~$ mount
/dev/hda4 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
tmpfs on /lib/modules/2.6.12-10-386/volatile type tmpfs (rw,mode=0755)
/dev/hda2 on /media/windows type ntfs (rw,nls=utf8,umask=0222)
tmpfs on /dev type tmpfs (rw,size=10M,mode=0755)
ubuntu27@heaven:~$
```

---

### Post by ubuntu27 on 2006-01-25
***ignore this*** [Double post]

---

### Post by Limulus on 2006-01-25
[QUOTE=ubuntu27]It says “extended 3”
/dev/hda4 on / type ext3 (rw,errors=remount-ro)
[/QUOTE]
So the kernel was giving out wrong info on your partition... sounds like a bug :)

Well, that's one less mystery to solve ^_^

---

