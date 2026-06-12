---
title: "Hyper threading and Ubuntu"
date: 2006-01-16
forum: General Help
---

### Post by ashokpappu on 2006-01-16
Hello All,
I installed ubuntu 5.04 on my P4 3.0GHz with Ht technology(Dell dimension 8300).  I enabled HT in my bios but for some reasom the SMP kernel is not installed on my system.. when I install FC4 it is using the smp kernel.  what should I do to enable my ubuntu to take advantage of HT technology and use smp kernel?
Please advise
Thanks
Ashok Pappu

---

### Post by duffydack on 2006-01-16
Is it breezy or hoary?  Im interested to know bcoz i cant use any kernel higher than 2.6.10.x.x.x with HT enabled in any linux distro (well i only tried suse10 and breezy/hoary).  the system lags like hell in suse10/breezy, as their default kernels are higher 2.6.10, and hoary is fine with it being on 2.6.10, but lacks all the latest packages now in its repos.  Breezy also takes an entire age to boot.

well back to the issue, type sudo apt-get install linux-686-smp and append ht=on to your /boot/grub/menu.lst file, the long kernel line.
cant give you exact string as im not using linux at the moment.
let me know if you try breezy and use HT, my inspiron 9100 3.2ghz HT enabled doesnt do great.

---

### Post by JuanFerS on 2006-01-16
I use 2.6.12-10-686-smp on Mobile P4... it doesn't lag or anything...

It's a 3.2 HT.

---

### Post by mips on 2006-01-17
Correct me if I'm wrong but HT has nothing to do with SMP. SMP is applicable to dual core or multiple processor systems.

---

### Post by briancurtin on 2006-01-17
[QUOTE=mips]Correct me if I'm wrong but HT has nothing to do with SMP. SMP is applicable to dual core or multiple processor systems.[/QUOTE]
that is what i figured as well, but i was told to check out the SMP kernel with my P4-HT and have had good results out of it. it may or may not be actually doing anything, but it seems to work better to me

---

### Post by limit223 on 2006-01-17
" 01 Jan 2003

    The Intel Xeon processor introduces a new technology called Hyper-Threading (HT) that, to the operating system, makes a single processor behave like two logical processors. When enabled, the technology allows the processor to execute multiple threads simultaneously, in parallel within each processor, which can yield significant performance improvement. We set out to quantify just how much improvement you can expect to see."

Plenty of info just for a simple search on the internet!

[http://www-128.ibm.com/developerworks/linux/library/l-htl/](http://www-128.ibm.com/developerworks/linux/library/l-htl/)

---

### Post by thespinesplitter on 2006-01-17
coreection: HT is a form of SMP but 32 bit only

---

### Post by mips on 2006-01-18
Thanks for that.

---

### Post by duffydack on 2006-01-20
dont forget to add ht=on to your grub boot

---

### Post by colsinc on 2006-03-28
where exactly does ht=on go in the menu.lst file?

> # menu.lst - See: grub(8), info grub, update-grub(8)
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
timeout		3

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
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/sda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

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
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST


---

### Post by feathers on 2006-03-28
The only thing I have ever did was to install a kernel with -smp at the end and it has worked since then.
Now, in dapper, smp support is in the normal kernel. There are no smp-kernels any more. If you want to know how the 2 cpu's are working you could install gkrellm.

---

### Post by Bukunut on 2006-03-28
Do you need ht=on on your grub list if you have the SMP kernel installed?
Correct me if I am wrong but if you do the following in console :-

$ *grep processor /proc/cpuinfo*

The following results show that HT is switched on?

[I]processor       : 0
processor       : 1[/I]

Bukunut.

---

### Post by feathers on 2006-03-28
[QUOTE=Bukunut]Do you need ht=on on your grub list if you have the SMP kernel installed?[/Quote]
No, you do not have to.
> 
Correct me if I am wrong but if you do the following in console :-

$ *grep processor /proc/cpuinfo*

The following results show that HT is switched on?

[I]processor       : 0
processor       : 1[/I]

Bukunut.

It does exactly mean that. You have two processors, processor 0 and processor 1. As with most cases, computers start counting with zero.

---

### Post by Bukunut on 2006-03-28
Feathers

Thank you for confirming these for me. :D  This is the result of HT with Pentium 4 single processor, I am not sure I have seen much speed increase at all. Maybe it's just me ...

Regards - Bukunut

---

### Post by OzzOzzOzz on 2006-08-27
I also recently just installed Ubuntu and the smp kernel.

If you complaining about sluggishness and lagging, then you can try this:

Change your graphics driver.

I am using a P4 3.00Ghz with HT and integrated graphics.
I changed 'vesa' to 'sis' (for sis graphics) in XOrg conf.

Restart X and you won't believe the difference.

Anyway, let me know if this helps.

Cheers
Ozz

---

### Post by FBorges22 on 2006-09-27
Hello there,

I need to know where exactly does ht=on go in the menu.lst file... I am not understanding... please, I need a tip.

---

