---
title: "&quot;Optimizing Kernel&quot; leades to panic!"
date: 2005-08-17
forum: Desktop Environments
---

### Post by Grafster on 2005-08-17
Hi there.

I tried a bunch of searches but I couldn't find anyone posts addressing this problem....
I followed these directions
[http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#Enabling_an_Optimized_Kernel](http://digital-conquest.ath.cx/wiki/index.php/Ubuntu#Enabling_an_Optimized_Kernel)

and now whenever I turn on the computer i get "kernel panic!" and the system hangs mid-boot.

The grub menu allows me to boot on a  the 386 version. 

uname -a returns:
Linux Grafnet 2.6.10-5-386 #1 Fri Jun 24 16:53:01 UTC 2005 i686 GNU/Linux

I have a pentium, though I can't recal the exact flavor its relatively recent.

Edit= orphaned fragment

---

### Post by pmjdebruijn on 2005-08-17
Hi,

Which optimization did you use? I assume this one:
sudo apt-get install linux-686 linux-restricted-modules-686 nvidia-glx

Anyway that should work for Pentium Pro, Pentium II, Pentium III, and so on... Just not on a normal Pentium or on a AMD K6...

Anyway your post is way to vague... "Kernel panic" can mean just about anything... Really... So what did it say before kernel panic? The kernel doesn't just panic, there's a reason for that... and usually it's displayed onscreen!

Please post your /boot/grub/menu.lst in here...

Also, you can see what processor you have, by typing 'cat /proc/cpuinfo'.

Regards,
Pascal de Bruijn

---

### Post by Grafster on 2005-08-17
The optimization I got (from the link in the first post) was
sudo apt-get install linux-686 linux-restricted-modules-686 nvidia-glx

Superfast responce. Very cool. Restarting computer now to get specific info.

vendor_id       : GenuineIntel
cpu family      : 15
model           : 3
model name      : Intel(R) Pentium(R) 4 CPU 2.80GHz

(sorry this is so long)
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
## by the debian update-grub script except for the default optons below

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

title		Ubuntu, kernel 2.6.10-5-686 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-686 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-686 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.10-5-686
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/sda1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/sda1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by Grafster on 2005-08-17
Ok so it starts to boot

after the grub menu thing it chatters for a bit and then
(stuff in paraenthesis is where I've edited)

Call Trace
[<c021ff36>] pcicbios_fid_device 40x27/0x50
(this goes on for 8 lines or so)
[<c010127d>] kernel_thread_helper+0x5/0xb
Code: (string of 2 digit numbers)
<0> kernel panic - not syncing. Attempted to kill init!

Gotta run to work but I can transcribe in more detail later if it will be helpful.

[Edit= fixed a misspelling of attempted.]

---

### Post by Grafster on 2005-08-18
Should I assume that people need more from the Kernel reboot?
If so what? (the long string of two digit numbers? the [<c0xxxx>] lines?)

Does "not syncing" or "Attempted to kill init!" mean anything?

---

### Post by Grafster on 2005-08-20
I realize that digging into someone else's weird hardware problems is none-ones idea of a good time.

Could someone at least suggest a way that I can get rid of the non-functioning Kernel program? (i.e. so it isn't default and isn't lying around on my system).

I'll avoid out and out groveling for a responce for another day or so, but I assure you its a terrible sight.

---

### Post by Velox Letum on 2005-08-20
```
sudo dpkg -r kernel-image-2.6.10-5
```

I believe this is how you remove the kernel, however don't quote me on it...I rarely remove kernels.

---

