---
title: "Can't get into Win XP"
date: 2009-03-01
forum: General Help
---

### Post by MikeHimself on 2009-03-01
Hi.

I am running Win XP and Heron on the same PC.
XP is on Drive D, Heron on E
This has worked well for several months.
This morning I switched on and it skipped the menu and went straight into Ubuntu without giving me option to choose the Windows loader. I tried to restarting several times.
Please can anyone suggest a safe solution.
Most of my saved work is on Windows, so I don't mind deleting and reinstalling Ubuntu - if that is the best option.

Regards, Mike.

---

### Post by woosey on 2009-03-01
Hi Mike,

Can you post up the result of -

```

cat /etc/grub.conf

```

---

### Post by MikeHimself on 2009-03-01
mike@mike-desktop:~$ cat /etc/grub.conf
cat: /etc/grub.conf: No such file or directory

---

### Post by pfdevil on 2009-03-01
I think what your looking for is: ```
 cat /boot/grub/menu.lst
```

---

### Post by woosey on 2009-03-01
> **pfdevil said:**
> I think what your looking for is: ```
 cat /boot/grub/menu.lst
```

quie correct, sorry was in centos mode ;)

---

### Post by Yownanymous on 2009-03-01
> **woosey said:**
> quie correct, sorry was in centos mode ;)

Away! Away with your vile enterprise distribution! :P

---

### Post by pfdevil on 2009-03-01
:lolflag:

---

### Post by woosey on 2009-03-01
> **Yownanymous said:**
> Away! Away with your vile enterprise distribution! :P

:p I work for an ISP, so i'm afraid im more use to RHE and centos ;)

---

### Post by MikeHimself on 2009-03-01
Having trouble posting result as I get the following -

[I]You have included 14 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

Images include use of smilies, the BB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.[/I]

Trying to split it into two messages. Watch this space!

---

### Post by MikeHimself on 2009-03-01
Result Part 1

---

### Post by pfdevil on 2009-03-01
Put your output in the [CODE] tags, look for the #.

---

### Post by MikeHimself on 2009-03-01
Result Part 2

---

### Post by MikeHimself on 2009-03-01
Result Part 3

---

### Post by MikeHimself on 2009-03-01
OK Got it!

M.


```
mike@mike-desktop:~$  cat /boot/grub/menu.lst

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

# kopt=root=UUID=2fd63729-5d70-4319-8606-bf24542ebdb4 ro



## Setup crashdump menu entries

## e.g. crashdump=1

# crashdump=0



## default grub root device

## e.g. groot=(hd0,0)

# groot=(hd0,8)



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



title		Ubuntu 8.04.1, kernel 2.6.24-23-generic

root		(hd0,8)

kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=2fd63729-5d70-4319-8606-bf24542ebdb4 ro quiet splash

initrd		/boot/initrd.img-2.6.24-23-generic

quiet



title		Ubuntu 8.04.1, kernel 2.6.24-23-generic (recovery mode)

root		(hd0,8)

kernel		/boot/vmlinuz-2.6.24-23-generic root=UUID=2fd63729-5d70-4319-8606-bf24542ebdb4 ro single

initrd		/boot/initrd.img-2.6.24-23-generic



title		Ubuntu 8.04.1, kernel 2.6.24-22-generic

root		(hd0,8)

kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=2fd63729-5d70-4319-8606-bf24542ebdb4 ro quiet splash

initrd		/boot/initrd.img-2.6.24-22-generic

quiet



title		Ubuntu 8.04.1, kernel 2.6.24-22-generic (recovery mode)

root		(hd0,8)

kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=2fd63729-5d70-4319-8606-bf24542ebdb4 ro single

initrd		/boot/initrd.img-2.6.24-22-generic



title		Ubuntu 8.04.1, kernel 2.6.24-21-generic

root		(hd0,8)

kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2fd63729-5d70-4319-8606-bf24542ebdb4 ro quiet splash

initrd		/boot/initrd.img-2.6.24-21-generic

quiet



title		Ubuntu 8.04.1, kernel 2.6.24-21-generic (recovery mode)

root		(hd0,8)

kernel		/boot/vmlinuz-2.6.24-21-generic root=UUID=2fd63729-5d70-4319-8606-bf24542ebdb4 ro single

initrd		/boot/initrd.img-2.6.24-21-generic



title		Ubuntu 8.04.1, kernel 2.6.24-19-generic

root		(hd0,8)

kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2fd63729-5d70-4319-8606-bf24542ebdb4 ro quiet splash

initrd		/boot/initrd.img-2.6.24-19-generic

quiet



title		Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)

root		(hd0,8)

kernel		/boot/vmlinuz-2.6.24-19-generic root=UUID=2fd63729-5d70-4319-8606-bf24542ebdb4 ro single

initrd		/boot/initrd.img-2.6.24-19-generic



title		Ubuntu 8.04.1, memtest86+

root		(hd0,8)

kernel		/boot/memtest86+.bin

quiet



### END DEBIAN AUTOMAGIC KERNELS LIST



# This is a divider, added to separate the menu items below from the Debian

# ones.

title		Other operating systems:

root





# This entry automatically added by the Debian installer for a non-linux OS

# on /dev/sda1

title		Windows NT/2000/XP (loader)

root		(hd0,0)

savedefault

makeactive

chainloader	+1


```

---

### Post by MikeHimself on 2009-03-01
But I still can't get into Windows......

---

### Post by MikeHimself on 2009-03-02
Hi.

Is anyone there? Or have I passed beyond the event horizon?
Would it just be easier to delete Ubuntu? I need an easy answer, please.

---

### Post by sahabcse on 2009-03-02
Hi 

Try to Fix the grub. Follow the below url

=============================================
[http://sahabm.blogspot.com/2009/01/grub-fix-windows.html](http://sahabm.blogspot.com/2009/01/grub-fix-windows.html)
[http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html](http://sahabm.blogspot.com/2009/01/grub-fix-ubuntu.html)
=============================================

Regards,
Sahab

---

### Post by alphane on 2009-03-02
probably not the best solution, but on my last install, grub managed to get the wrong hard drive and partition for my menu.lst resulting in grub error 13 (no bootable os)

I didn't know what HD i'd installed windows on (at least in terms of HD numbering) so what I did was press 'e' at grub menu on my windows xp entry ( I think it's 'e', the key to edit the command ) and edited my grub entry numbers until I struck gold.

Assuming you only have one physical hard drive and many paritions, the line that reads

```
root		(hd0,0)
```

I would edit the second 0 to 1 or 2 or 3 or 4 etc see if you get into windows.

editing the grub entry like this is not permanent, the next time you reboot your machine you will again be back at 0,0 so you wont screw anything up.

Not the most elegant solution, you'd probably be better looking through your fstab file for the actual NTFS partition position or something, but someone else will be better equipped to help you there.

---

### Post by caljohnsmith on 2009-03-02
In order to get a clearer picture of your setup related to booting Windows, how about downloading the **Boot Info Script** to your Ubuntu desktop:

[https://sourceforge.net/projects/bootinfoscript/](https://sourceforge.net/projects/bootinfoscript/)

Then open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of the RESULTS.txt file to your next post, highlight the copied text, and click the pound/hash sign "#" graphic button in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what the solution to your booting problem might be.

---

### Post by MikeHimself on 2009-03-02
[COLOR="Red"]Hi.

I think I have found the answer to my problem.

I have been having trouble with my CMOS.
Changing the battery only partially cured it.
It still comes back with a bad checksum from time to time.
Last time that happened I couldn't be bothered to reset the BIOS, so just hit "Restore default values". 
I suspect this was the cause of the problem.
I have reset my BIOS and now get the menu options - and get back into Windows.

Thanks to all who have offered help.

Best regards, Mike.[/COLOR]

---

