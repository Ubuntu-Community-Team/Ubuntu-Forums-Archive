---
title: "Putting a password on Ubuntu boot sequence"
date: 2008-12-18
forum: General Help
---

### Post by lachie on 2008-12-18
Hey,

(this is my first post)
i want to put a password on Ubuntu in the boot sequence. i know how to get into menu.lst to change things.
i put the password thing into the boot sequence and changed the password to what i wanted but when i booted it said 

Error: 32
Must be authenticated

what do i do to make it work so my brother cant get into Ubuntu and screw up everything


Cheers lachie

---

### Post by PocketDog on 2008-12-18
[http://www.gnu.org/software/grub/manual/html_node/Security.html](http://www.gnu.org/software/grub/manual/html_node/Security.html) Hope that helps.

---

### Post by lachie on 2008-12-20
thanks for that but unbfortunatley it still says:

Error: 32
Must be authenticated

when i boot. but any other help would be great

Cheers lachie

---

### Post by monkeyking on 2008-12-21
I can't really help you since I don't know what it is you want excatly.
Why do you need a passwd to a boot sequenze?
Is it from the grub menu,
or from a startup script.
you need the password

I've been using expect for something like this [http://en.wikipedia.org/wiki/Expect](http://en.wikipedia.org/wiki/Expect)


Can you elaborate on what your are trying to accomplish.

good luck

---

### Post by kellemes on 2008-12-21
> **lachie said:**
> Hey,

(this is my first post)
i want to put a password on Ubuntu in the boot sequence. i know how to get into menu.lst to change things.
i put the password thing into the boot sequence and changed the password to what i wanted but when i booted it said 

Error: 32
Must be authenticated

what do i do to make it work so my brother cant get into Ubuntu and screw up everything


Cheers lachie

Just give your brother the permissions he needs to use Ubuntu without being able to screw things up.

---

### Post by Denestria on 2008-12-21
> **lachie said:**
> Error: 32
Must be authenticated


It says that after you've done what?  When you select an entry in grub?  After you have entered the password and tried to boot the selection?

If you are hitting enter on an entry and expecting a password prompt it doesn't work that way.  You need to press 'p' in the grub menu then enter the password.

---

### Post by abhilashm86 on 2008-12-21
did u become super user or sudo to edit changes in menu.lst?save it before exit,may be a small error

---

### Post by lachie on 2008-12-22
> **kellemes said:**
> Just give your brother the permissions he needs to use Ubuntu without being able to screw things up.

yeah mabey. Probolem is he could crash a read and write childerens toy!

Lachie

---

### Post by lachie on 2008-12-22
> **abhilashm86 said:**
> did u become super user or sudo to edit changes in menu.lst?save it before exit,may be a small error

yes i did

Lachie

---

### Post by bodhi.zazen on 2008-12-22
First, IMO, all this is a bit of a waste and most security measures can be easily defeated if one has physical access.

This feature is easily changed with any live cd, just mount the boot partition and undo the changes ...

Encryption will not help as the /boot partition is not encrypted.

With that said, when you boot, hit the p key on the key board and enter your password.

---

### Post by lachie on 2008-12-23
ok ill explain in detail because i was a bit unclear.

i opened terminal and typed in:
sudo gedit /boot/grub/menu.lst

i changed te boot sequence so it read:
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		c9fbffd8-99bd-4823-a5f6-238224eeffce
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=c9fbffd8-99bd-4823-a5f6-238224eeffce ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet
[COLOR="Red"]password topsecret
password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/[/COLOR]

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		c9fbffd8-99bd-4823-a5f6-238224eeffce
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=c9fbffd8-99bd-4823-a5f6-238224eeffce ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, memtest86+
uuid		c9fbffd8-99bd-4823-a5f6-238224eeffce
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

then i booted up ubuntu and it said:

bla bla bla booting ubuntu (or whatever)
Password:

i entered my password and the computer said:

Error: 32
Must be authenticated

i want to be able to use a password without the computer giving me an error




is that clearer?


Cheers Lachie

---

### Post by lachie on 2008-12-23
i opened terminal and typed in:
sudo gedit /boot/grub/menu.lst

i changed te boot sequence so it read:
## ## End Default Options ##

title Ubuntu 8.10, kernel 2.6.27-9-generic
uuid c9fbffd8-99bd-4823-a5f6-238224eeffce
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=c9fbffd8-99bd-4823-a5f6-238224eeffce ro quiet splash
initrd /boot/initrd.img-2.6.27-9-generic
quiet
[COLOR="Red"]password topsecret
password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/[/COLOR]

title Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid c9fbffd8-99bd-4823-a5f6-238224eeffce
kernel /boot/vmlinuz-2.6.27-9-generic root=UUID=c9fbffd8-99bd-4823-a5f6-238224eeffce ro single
initrd /boot/initrd.img-2.6.27-9-generic

title Ubuntu 8.10, memtest86+
uuid c9fbffd8-99bd-4823-a5f6-238224eeffce
kernel /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

then i booted up ubuntu and it said:

bla bla bla booting ubuntu (or whatever)
Password:

i entered my password and the computer said:

Error: 32
Must be authenticated

i want to be able to use a password without the computer giving me an error




is that clearer?


Cheers Lachie

---

### Post by joshmuffin on 2008-12-23
Hello.

If your duel booting and other people want to acsess a different OS then discard my post.

Do you have a log-in password but if your worried he will go to root prompt ect.?

If you want to lock him out of GRUB then consider a BIOS password. There easy as to set.

Hope I helped, Joshmuffin.

---

### Post by lachie on 2009-01-07
sorry i havent replyed earlier but ive been tied up in so many random things. if i put a password on the BIOS wont it lock other users out of both Operating Systems ?

lachie

PS how do you put a password on ? i had a look but i couldnt find anything

---

### Post by monkeyking on 2009-01-07
there are normally 2 kind of bios passwds.

1. boot passwd
2. bios passwd

boot passwd is a code you'll need to enter just to start the computer.
bios passwd is a code you'll need to enter to change bios.

This has nothing to do with the operation system.

---

### Post by lachie on 2009-01-24
thanks but all i want to do is put a password on the booting of Ubuntu

Lachie

---

### Post by lachie on 2009-01-24
thanks but all i want to do is put a password on the booting of Ubuntu

Lachie

---

### Post by mb_webguy on 2009-01-25
Hrm... I'm pretty sure you shouldn't have two separate password entries in the menu.lst file.  Either you have an unencrypted password or an md5 encrypted password.  Comment one of them out and see if that works.

---

### Post by lachie on 2009-02-04
ok i think this is too hard, ill just use a BIOS password

lachie

---

### Post by mb_webguy on 2009-02-05
You had everything correct except you had two different password entries in GRUB, and had it in the wrong place.  Here's my GRUB menu.lst.  I've put the relevant sections in bold:
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
default		1

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
password --md5 $1$ww8Fu$LnzkRYK0d2ZEdBfvZH1.70

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


title		Ubuntu 8.10, kernel 2.6.27-11-generic (console)
uuid		0464a80e-a119-471b-ac99-7a541c4f8166
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=0464a80e-a119-471b-ac99-7a541c4f8166 ro quiet splash text
initrd		/boot/initrd.img-2.6.27-11-generic
quiet


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
# kopt=root=UUID=0464a80e-a119-471b-ac99-7a541c4f8166 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=0464a80e-a119-471b-ac99-7a541c4f8166

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# **lockalternative=true**

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# **lockold=true**

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
# howmany=2

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
uuid		0464a80e-a119-471b-ac99-7a541c4f8166
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=0464a80e-a119-471b-ac99-7a541c4f8166 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
**lock**
uuid		0464a80e-a119-471b-ac99-7a541c4f8166
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=0464a80e-a119-471b-ac99-7a541c4f8166 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
**lock**
uuid		0464a80e-a119-471b-ac99-7a541c4f8166
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0464a80e-a119-471b-ac99-7a541c4f8166 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
**lock**
uuid		0464a80e-a119-471b-ac99-7a541c4f8166
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=0464a80e-a119-471b-ac99-7a541c4f8166 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		0464a80e-a119-471b-ac99-7a541c4f8166
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista
root		(hd0,0)
makeactive
chainloader	+1
**lock**
```

The only entries I don't need a password to use are the regular Ubuntu login, the console login I added before the automagic kernels section, and the memtest option.  The alternate and old boot options are locked by the lockalternatives and lockold options in the automagic kernels section (which are applied automatically when you change those options then run "sudo update-grub" from the command line).  The Windows boot entry I manually locked by adding the "lock" line.

Notice I only have one password entry uncommented.  The two separate examples are showing you two different ways of using a password, either unencrypted or encrypted.  You should use one or the other, but not both.

To boot using a locked entry, you have to hit the "p" key at the GRUB menu and enter the password.

---

