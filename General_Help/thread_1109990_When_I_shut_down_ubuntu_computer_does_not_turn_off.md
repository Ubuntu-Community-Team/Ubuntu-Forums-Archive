---
title: "When I shut down ubuntu computer does not turn off by itself."
date: 2009-03-29
forum: General Help
---

### Post by kevincolorado on 2009-03-29
When I shut down ubuntu computer does not turn off by itself.  How do I change this?

Thank You

---

### Post by 3Miro on 2009-03-29
What happens, there is a way to make it show details on shutdown. I just don't know how :) ?

---

### Post by CatKiller on 2009-03-29
That functionality is provided by ACPI. It needs to be supported and enabled in the BIOS of the computer, and in the OS. It is possible to enable or disable this option on the BIOS configuration screen, and it is possible to enable or disable it in Linux in the kernel line of GRUB's menu.lst. If ACPI is disabled in either of these places, your computer will not automatically turn off when it's shut down.

---

### Post by CatKiller on 2009-03-29
menu.lst is at **/boot/grub/menu.lst**. You can read the contents with ```
less /boot/grub/menu.lst
``` or edit  them with ```
sudo nano /boot/grub/menu.lst
```

---

### Post by DeMus on 2009-03-29
> **CatKiller said:**
> menu.lst is at **/boot/grub/menu.lst**. You can read the contents with ```
less /boot/grub/menu.lst
``` or edit  them with ```
sudo nano /boot/grub/menu.lst
```

Yeah??? And what to write into the menu.lst file??

---

### Post by koanhead on 2009-03-29
Don't write anything in it yet. Just post it here for starters, along with the output of dmesg.
If you aren't sure how to do that, try this:

Code:

touch newfilename
dmesg > newfilename


Then attach the file to your next post. This will help us diagnose the problem.

Sorry I don't know how to make those little "Code:" boxes. I'll figure it out eventually I guess, and then my posts will be more pretty ;)

---

### Post by DeMus on 2009-03-29
> **koanhead said:**
> 

Sorry I don't know how to make those little "Code:" boxes. I'll figure it out eventually I guess, and then my posts will be more pretty ;)

Use the buttons on top of this edit field. Place the mouse over them and wait until the little help appears. It's quite simple, even I understand it. :P

---

### Post by VCoolio on 2009-03-29
Check [this]("http://ubuntuforums.org/showthread.php?t=1107955&highlight=shutdown+power&page=2") thread, post 19. If your issue is the same this should solve it. 
Edit: this is for Jaunty, so I guess this won't solve it.
I found after some searching what worked for me. It is [here]("http://www.thinkwiki.org/wiki/Install_Ubuntu_8.10_%28Intrepid_Ibex%29_on_a_Thinkpad_T400#Shutdown_freezes_sometimes"). This solved my problem that the shutdown hangs and pc is not powered off. Btw, where it says "sudo gedit" etc, use "gksudo gedit". For gui-applications it is best to use gksudo.

Btw, the command 
```
sudo shutdown -hP now
```
works too. You can make a launcher with 'gksudo shutdown -hP now' as command to use as long as you haven't fixed your problem.

---

### Post by CatKiller on 2009-03-29
> **koanhead said:**
> Sorry I don't know how to make those little "Code:" boxes. I'll figure it out eventually I guess, and then my posts will be more pretty ;)

Yeah, there isn't the Code button on the Quick Reply box like there is on the full Edit mode box, even though there is an Add Image button for reasons that completely escape me :rolleyes:

For reference, the button puts [CODE] and its complement around the text to signify the Code box.

---

### Post by CatKiller on 2009-03-29
> **DeMus said:**
> Yeah??? And what to write into the menu.lst file??

I only mentioned it because the OP PMed me to ask where menu.lst was. If the kernel line has *acpi=off*, then obviously ACPI won't work. I believe there are also related APM options for those BIOSes that have problems. *apm=off* does the obvious, but I seem to recall that *power_off* and *realmode_power_off* are also valid apm options. Can't remember what the difference between them is at the moment, though.

And of course, if APM and ACPI are disabled in the BIOS, then it doesn't really matter what the options are set to in GRUB. As VCoolio points out, it's also possible to fiddle with these options with the appropriate kernel modules' respective options.

Hopefully when the OP follows koanhead's advice and posts some more information here someone can help to pinpoint why their computer isn't powering down.

---

### Post by kevincolorado on 2009-03-29
Here is my menu.lst

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
# kopt=root=UUID=dceb7b4c-f3b9-47e6-9b3b-cefaf374ddd1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=dceb7b4c-f3b9-47e6-9b3b-cefaf374ddd1

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
uuid		dceb7b4c-f3b9-47e6-9b3b-cefaf374ddd1
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=dceb7b4c-f3b9-47e6-9b3b-cefaf374ddd1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		dceb7b4c-f3b9-47e6-9b3b-cefaf374ddd1
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=dceb7b4c-f3b9-47e6-9b3b-cefaf374ddd1 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		dceb7b4c-f3b9-47e6-9b3b-cefaf374ddd1
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=dceb7b4c-f3b9-47e6-9b3b-cefaf374ddd1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		dceb7b4c-f3b9-47e6-9b3b-cefaf374ddd1
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=dceb7b4c-f3b9-47e6-9b3b-cefaf374ddd1 ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		dceb7b4c-f3b9-47e6-9b3b-cefaf374ddd1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dceb7b4c-f3b9-47e6-9b3b-cefaf374ddd1 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		dceb7b4c-f3b9-47e6-9b3b-cefaf374ddd1
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=dceb7b4c-f3b9-47e6-9b3b-cefaf374ddd1 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		dceb7b4c-f3b9-47e6-9b3b-cefaf374ddd1
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

---

