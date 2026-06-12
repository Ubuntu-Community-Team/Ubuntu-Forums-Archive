---
title: "Doing a dual boot: ubuntu - Windows XP Pro"
date: 2005-12-15
forum: Desktop Environments
---

### Post by ADNoland on 2005-12-15
I decided I'd like to try and dual boot. I know next to nothing about linux so this probably wasn't a good start for me :razz: I've attempted to search the forums for something related and I googled it, but didn't come up with anything that I completely understood. I figured I'd come here since it's specific to the Ubuntu OS. I appreciate any help or definitly any help links for this. I probably should have come here before I did anything, but I didn't so everything is kind of jacked up:razz: I was able to back up some files but not all. Maybe you guys can either help me get the mess sorted out or tell me how I can correct do a dual boot;) 

I was talking with a friend of mine and explained the problem to him. To save time I'll copy and paste here what's going on :(

__________________
Grub loads up, gives me the options for linux or XP Pro, It begins loading XP pro, it goes through it loadup cycle (black screen, scrolling blue bar) and then goes to another screen where it looks for chkdsk and another program.. partition magic I think, then it restarts itself.

Well, not being familiar with the program I'll tell you what I can remember. I used an option in partiton magic 8.05 called "install a new OS" or something along those lines. I had created a small 20gig partition out of my main HD. I set the file system to ect2? I hit apply and let it restart and do its thing. I let it restart I got an OS could not be found error, so I knew the problem was it was booting from HD instead of disk. I swapped the bootup paramaters so the CD would be read before the HD. I began installing Ubuntu. I came to the format partition screen, the automatic options were to delete everything on disc and install it there, obviously I didn't want everything deleted so I went to do it manual. I did the best I could and came up with these settings.

I changed the main HD partition (with XP) to not be mounted.
Next was the Swap partition, I left it alone,
Next was my Linux partition that I had created, I believe it was simply listed as /
Last was my secondary hard drive, I also put it to not be mounted.

After this, I let it install, then I tried to boot up windows, just to see if it would run, then I started up with the problem I'm having. The computer rebooted and I let it boot up Ubuntu which I'm now it, the only failed message I seen was it apparantly couldnt find the ect2(ext2??) partition, but it kept booting and thats the only failure message I remember seeing. I can't think of any more details right now.

Any questions I will answer best as I can. I appreciate everyone atleast taking the time to read this. I'd rather not reinstall XP but if I have to I'd like to know how to correctly do a dualboot system.

---

### Post by tburns on 2005-12-15
[QUOTE=ADNoland]I decided I'd like to try and dual boot. I know next to nothing about linux so this probably wasn't a good start for me :razz: I've attempted to search the forums for something related and I googled it, but didn't come up with anything that I completely understood. I figured I'd come here since it's specific to the Ubuntu OS. I appreciate any help or definitly any help links for this. I probably should have come here before I did anything, but I didn't so everything is kind of jacked up:razz: I was able to back up some files but not all. Maybe you guys can either help me get the mess sorted out or tell me how I can correct do a dual boot;) 

I was talking with a friend of mine and explained the problem to him. To save time I'll copy and paste here what's going on :(

__________________
Grub loads up, gives me the options for linux or XP Pro, It begins loading XP pro, it goes through it loadup cycle (black screen, scrolling blue bar) and then goes to another screen where it looks for chkdsk and another program.. partition magic I think, then it restarts itself.

Well, not being familiar with the program I'll tell you what I can remember. I used an option in partiton magic 8.05 called "install a new OS" or something along those lines. I had created a small 20gig partition out of my main HD. I set the file system to ect2? I hit apply and let it restart and do its thing. I let it restart I got an OS could not be found error, so I knew the problem was it was booting from HD instead of disk. I swapped the bootup paramaters so the CD would be read before the HD. I began installing Ubuntu. I came to the format partition screen, the automatic options were to delete everything on disc and install it there, obviously I didn't want everything deleted so I went to do it manual. I did the best I could and came up with these settings.

I changed the main HD partition (with XP) to not be mounted.
Next was the Swap partition, I left it alone,
Next was my Linux partition that I had created, I believe it was simply listed as /
Last was my secondary hard drive, I also put it to not be mounted.

After this, I let it install, then I tried to boot up windows, just to see if it would run, then I started up with the problem I'm having. The computer rebooted and I let it boot up Ubuntu which I'm now it, the only failed message I seen was it apparantly couldnt find the ect2(ext2??) partition, but it kept booting and thats the only failure message I remember seeing. I can't think of any more details right now.

Any questions I will answer best as I can. I appreciate everyone atleast taking the time to read this. I'd rather not reinstall XP but if I have to I'd like to know how to correctly do a dualboot system.[/QUOTE]

You might be happier if you dual boot with a second hdd rather than repartitioning an existing windows drive. Then you won't have to mess with one os to get the other on. Say you have windows installed on /hda and linux on /hdb. When ubuntu gets around to doing the grub config install, put it in the mbr (as prompted by the installer). I have killed and reinstalled linux several times while dual booting with windows. I haven't messed up windows yet.  

I can't remember how windows xp installs (if you are planning a windows reinstall), but you may need to cfdisk your drive before you start. Create a ntfs partition and leave the rest as empty unused space, you can create your ubuntu and swap partition during ubuntu install. Also, both the windows partition and ubuntu partition need to be bootable.

---

### Post by art on 2005-12-15
please post your /etc/fstab file.

---

### Post by ADNoland on 2005-12-15
Well, I deal with windows, but I'm not exactly sure how serious this windows problem is. I don't know if I'm going to have to reinstall windows or not. I'd rather not. So if I just screwed something up in the ubuntu install maybe I can fix it by reinstalling Ubuntu :confused:

---

### Post by ADNoland on 2005-12-15
Art, you would have to guide me through that. Like I said, I don't have any linux experience :)

---

### Post by art on 2005-12-15
Open up terminal and type 

more /etc/fstab

---

### Post by tburns on 2005-12-15
[QUOTE=ADNoland]Art, you would have to guide me through that. Like I said, I don't have any linux experience :)[/QUOTE]

In the terminal
$sudo cp /etc/fstab $HOME/fstab.txt
$sudo chmod 666 $HOME/fstab.txt

Then you should be able to open it in gedit or someother text.

---

### Post by ADNoland on 2005-12-15
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda2       /               ext2    defaults,errors=remount-ro 0       1
/dev/hda3       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0


Theres the information you requested I believe

---

### Post by HarryMangurian on 2005-12-15
for starters-

You could boot into linux.  Use Synaptic to get a copy of GPARTED, which is a partition program.  See if there is anything bad with your boot disk partitions and use GPARTED to fix it.

---

### Post by Snipersnest on 2005-12-15
I'm dual booting XP and Ubuntu...been doing it for almost a year now. Works out really well and its so simple. Hope you have a good experience but remember ITS OK TO ASK FOR HELP..lol...so many people just give up without asking...don't be a quiter.

---

### Post by art on 2005-12-15
And also 

more /boot/grub/menu.lst

---

### Post by ADNoland on 2005-12-15
this is completely everything listed from that command 


andrew@24-151-199-145:~$ more /boot/grub/menu.lst
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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title           Ubuntu, kernel 2.6.12-9-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.12-9-386
savedefault
boot

title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.12-9-386
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by ADNoland on 2005-12-15
I don't know whats important or not so I listed it all:p

---

### Post by art on 2005-12-15
Do sudo gedit /boot/grub/menu.lst, and at the very end change

title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

to 

title Microsoft Windows XP Professional
**unhide (hd0,0)**
root (hd0,0)
savedefault
makeactive
chainloader +1

Reboot.Should work.

---

### Post by ADNoland on 2005-12-15
Its a read only file, I look around but didn't see anything for changing it from read only to an editable document.

---

### Post by art on 2005-12-15
Yeah, that's why you need an "sudo" in front of it, and it will ask for password, which should be your password. 

sudo gedit /boot/grub/menu.lst

---

### Post by ADNoland on 2005-12-15
Okay, thanks. Well, I did the edit. I'm going to restart now and see what happens.

---

### Post by ADNoland on 2005-12-15
I greatly appreciate everyones help. I'm currently in Windows writing this post. I hope I can learn some things about linux now and maybe help another guy down the line like you guys helped me:)

---

### Post by art on 2005-12-15
Great!

---

### Post by Rackerz on 2005-12-15
[QUOTE=ADNoland]I greatly appreciate everyones help. I'm currently in Windows writing this post. I hope I can learn some things about linux now and maybe help another guy down the line like you guys helped me:)[/QUOTE]

Great to see everything is working for you now. Just remember, don't be afraid to ask questions even if you feel they are stupid. We all remember being at that point sometime, when we started using Linux. Ubuntu is the best place to start!

---

### Post by Ruskie on 2005-12-15
From my experience, this is something like screwing the partition table... And it's not your "fault", but I had a VERY similar problem lately when using Pmagic to repartition the main hard disk. The difference is that I got blue screen with Windows kernel panic... A "bootfix" of my Windows installation cd made restart Windows, and I used a utility called Disk Patch to fix the partition table (loosing Linux, but I guess if I installed Grub for Windows I could have avoided it).
The problem, I think, lies in Pmagic. In any case, you don't need that stupid "Install a new OS" option of its. Just resize your windows partition and create the ext3 and swap partition the dimension you like, in windows, BEFORE starting linux installation.
Afterwards, in Linux, it recognize them and installs flawless into the partitions you have just created. Grub can then be installed wherever you like (even in master boot record of Windows disk), and it runs without problems.

---

### Post by Gurgeh on 2005-12-16
I tried to dual boot originally but there doesn't seem to be a specific option in Ubuntu's installer to do it. Suffice to say I ended up replacing my boot sector. I panicked and screwed about all the data I though i'd lost but then I noticed:

- My graphic card worked beautifully and the resolution was auto detected.
- My soundcard was immediately supported
- My internet connection worked
- & most importantly - theres one serious community here to back you up.

So I stuck with it, threw myself in at the deep end and I don't regret it. absolutely everything I ever did with windows I can do with Linux and I lost nothing. Gnome is a quirky and pretty experience and the tools supplied by Ubuntu make it formidable. The constant battle for functionality is annoying at times but by god its rewarding. You really do not take your computing experience forgranted and enjoy every second of it when ur running linux. So to sum up my experience: I am overly grateful for my forceful liberation from the mainstream and the microsoft corporation can suck my willy.

---

