---
title: "Can't restore GRUB after XP reinstall..."
date: 2005-06-15
forum: Desktop Environments
---

### Post by dolny on 2005-06-15
I'm really pissed off. The methods from this forums didn't work with Live CD (commands such as 'grub' didn't work at all). Eh... WHY DOES IT HAVE TO BE SO HARD? WHY 'RESCUE' alone doesn't rescue the GRUB? Like LILO?

How can I mount a partition from the installer? I used manual partitioning>chosen hda14(my boot) to mount it as boot but I didn't know how. Do i have to choose that this is an ext3 partition and then some mount option will appear? Rescue, grub-install etc. commands don't work with Kubuntu Live CD/Installation CD. DAAAAAAAAAAMN!!!

I thought it was going to be easier, like in Mandrake (I used 'rescue' with LILO and it always worked).

I would like to rescue GRUB from the installer cause the LIVE CD method seems not to work. Eh... how to mount that partitions again without reformating? And how do I know which of my like 14 partitions is the appropriate one? LOL. 14 partitions, I know ;) 

**PLEASE HELP**

---

### Post by Digitallysick on 2005-06-15
Grub for me is the hardest part of linux, id say your probably need to re install  ubuntu to get it right. Why re install xp to start with??

---

### Post by wellery on 2005-06-15
I have come across this a couple of times. I managed to use the cd to only install the bootloader again. I did get some error messages from the installer such as no partition to install or something similar but it can be done.

---

### Post by pietro_spina on 2005-06-15
HaHa 14! man you must be a worse distro junkie than me...

Have you tried this...
[http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation)

I suppose if I were in your position and the above link was no help, I would grab a handy live CD (one that will let me write to hard drives) and browse my various partitions. (for some reason I've always liked [KANOTIX](http://kanotix.com/info/index.php)  for this sort of forensics) take notes of what you have installed where....  look for /boot/grub/menu.lst files on your various partitions... [COLOR=DarkOrange]I think all you need to do is set the right partition bootable flag in the installers partition editor...[/COLOR]

OR maybe these diirections are a better fit...

1. Boot from a Live CD, like Ubuntu Live, Knoppix, Mepis, or similar.

2. Open a Terminal. Go SuperUser (that is, type "su"). Enter root passwords as necessary. (in kanotix you need to set the passwd for root yourself... 
use  
$ passwd root

3. Type "grub" which makes a GRUB prompt appear.

4. Type "find /boot/grub/stage1". You'll get a response like "(hd0)" or in my case "(hd0,3)". Use whatever your computer spits out for the following lines.

5. Type "root (hd0,3)".

6. Type "setup (hd0,3)". This is key. Other instructions say to use "(hd0)", and that's fine if you want to write GRUB to the MBR. If you want to write it to your linux root partition, then you want the number after the comma, such as "(hd0,3)".

7. Type "quit".

8. Restart the system. Remove the bootable CD.

cheers,
p

---

### Post by dolny on 2005-06-16
The grub command doesn't work in the terminal. grub-install or rescue doesn't work with Kubuntu Installation or Live CD... :( :( :(

---

### Post by wvslkr on 2005-06-16
Then open /boot/grub/menu.1st in an editor and fix it, or post it plus your partition setup and someone will probably try to help you if you chill a bit. :)  :)

---

### Post by dolny on 2005-06-16
I tried to use that method with ubuntu dir:

```
root@99-2:/home/ubuntu # mkdir ubuntu
root@99-2:/home/ubuntu # sudo mount /dev/hda7 ubuntu
root@99-2:/home/ubuntu # chroot ubuntu
bash: dircolors: command not found
root@99-2:/ # grub-install /dev/hda
/sbin/grub-install: line 399: sort: command not found
/sbin/grub-install: line 399: uniq: command not found
/sbin/grub-install: line 194: expr: command not found
/sbin/grub-install: line 483: expr: command not found
/sbin/grub-install: line 472: test: -gt: unary operator expected
/sbin/grub-install: line 485: test: -eq: unary operator expected
/sbin/grub-install: line 483: expr: command not found
/sbin/grub-install: line 472: test: -gt: unary operator expected
/sbin/grub-install: line 485: test: -eq: unary operator expected
/sbin/grub-install: line 483: expr: command not found
/sbin/grub-install: line 472: test: -gt: unary operator expected
/sbin/grub-install: line 485: test: -eq: unary operator expected
/sbin/grub-install: line 483: expr: command not found
/sbin/grub-install: line 472: test: -gt: unary operator expected
/sbin/grub-install: line 485: test: -eq: unary operator expected
/sbin/grub-install: line 483: expr: command not found
/sbin/grub-install: line 472: test: -gt: unary operator expected
/sbin/grub-install: line 485: test: -eq: unary operator expected
/sbin/grub-install: line 483: expr: command not found
/sbin/grub-install: line 472: test: -gt: unary operator expected
/sbin/grub-install: line 485: test: -eq: unary operator expected
/sbin/grub-install: line 483: expr: command not found
/sbin/grub-install: line 472: test: -gt: unary operator expected
/sbin/grub-install: line 485: test: -eq: unary operator expected
/sbin/grub-install: line 483: expr: command not found
/sbin/grub-install: line 472: test: -gt: unary operator expected
/sbin/grub-install: line 485: test: -eq: unary operator expected
/sbin/grub-install: line 502: which: command not found


    GNU GRUB  version 0.95  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]
grub> root (hd0,)

Error 12: Invalid device requested
grub> setup  --stage2=/boot/grub/stage2 --prefix=/boot/grub (hd0)

Error 12: Invalid device requested
grub> quit
root@99-2:/ #
```

this is what I get when I try to run grub from Live CD terminal (Kubuntu):

```
ubuntu@99-2:~$ sudo passwd root
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
ubuntu@99-2:~$ grub
bash: grub: command not found
ubuntu@99-2:~$

```

HELP ME :(

---

### Post by dolny on 2005-06-16
My GRUB:

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
# color cyan/blue white/blue

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
# kopt=root=/dev/hda7 ro quiet vga=0x314 splash

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,13)

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

title		Debian GNU/Linux, kernel 2.6.10-5-686 
root		(hd0,13)
kernel		/vmlinuz-2.6.10-5-686 root=/dev/hda7 ro quiet vga=0x314 splash 
initrd		/initrd.img-2.6.10-5-686
savedefault
boot

title		Debian GNU/Linux, kernel 2.6.10-5-686 (recovery mode)
root		(hd0,13)
kernel		/vmlinuz-2.6.10-5-686 root=/dev/hda7 ro quiet vga=0x314 splash single
initrd		/initrd.img-2.6.10-5-686
savedefault
boot

title		Debian GNU/Linux, kernel memtest86+ 
root		(hd0,13)
kernel		/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title  Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title  Microsoft Windows XP Professional
root  (hd0,0)
savedefault
makeactive
chainloader +1

```

My boot partition is on hda14 and / is on hda7. I was a newb when I was partitioning the disk ;) I didn't knew that 2 partitions would suffice ;>
Anyway I'm fighting with it for the second day !! :( Help... 

PS. How can I check my partition setup?

Seems like I'm gonna lost everything again... probably gonna switch back to Windows if it happens.

As for my fstab, it looks terribly. Totally different than it used to look:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda9       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0

```

I had like 14 partitions listed here.

---

### Post by wvslkr on 2005-06-16
See if this helps,[http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation).  If not will get back need sleep.
GL :)

---

### Post by dolny on 2005-06-16
No. I think thats it. My Linux adventure ends here after two great months. I'm so pissed off. Everything went ok until this. Seems that nobody can help me. This just sucks so much :(

I tried mounting the / , swap and boot partitions from the Installation CD and reinstalling GRUB but that didn't work (error when trying to reinstall GRUB). Why does it have to end in such stupid way. :(
Right now i have 'disk error/boot failure' when I turn on the computer.

---

### Post by dolny on 2005-06-16
Re-installed Windows again. It works. Through Kubuntu Installation CD I tried grub-install /dev/hda but again got the same error as I quoted above. PLEASE HELP. I don't want to give up.

---

### Post by DarkT on 2005-06-16
Erg I think most people have been there, ok try this instead if you still have kubuntu installed (excuse if you know some of this already, I'm trying to cover all bases). Boot the live cd and from a root terminal mkdirs for your kubuntu install in the mnt folder. So if you have /boot /home & / as seperate paritions you would mkdir for /mnt/kubuntu /mnt/kubuntu/boot /mnt/kubuntu/home (if /mnt/kubuntu already exists then call it something else)

You would then have to mount those partitions to the folders so lets say they are on  hda1 hda2 & hda3 (ide channel 1, drive 1, paritions 1, 2 & 3) respectively. So you would:
```

mount -t (reiserfs, ext3 or whatever your file system is) /dev/hda1 /mnt/kubuntu/ 
mount -t (file system) /dev/hda2 /mnt/kubuntu/boot
mount -t (file system) /dev/hda3 /mnt/kubuntu/home

```
If you encounter problems with it saying something is already mounted then just unmount it, this was probably automaticly done by the live cd.
So doing something along these lines should now have your kubuntu install mounted. Now you'll have to chroot to your install with something along the lines of:
```

chroot /mnt/kubuntu /bin/bash

```
This will then set it up so that the root of the terminal the /bin/bash starts is in fact  /mtn/kubuntu, your kubuntu install. From here you can now type something along the lines of (although you really want to quadruple check what your settings should be and twice read what you've typed ;))
```

grub-install /dev/hda

```
...something along those lines *should* work.
You then type exit to get out of the chrooted terminal and be taken back to the livecd terminal.
I really hope that helps :)

---

### Post by dolny on 2005-06-16
I'm going to read that now;) 

Anyway I found a backup of my old fstab:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda7       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda14      /boot           ext3    defaults        0       2
/dev/hdb2       /home           ext3    defaults        0       2
/dev/hda13      /opt            ext3    defaults        0       2
/dev/hda5       /srv            ext3    defaults        0       2
/dev/hda12      /tmp            ext3    defaults        0       2
/dev/hda8       /usr            ext3    defaults        0       2
/dev/hda11      /usr/local      ext3    defaults        0       2
/dev/hda10      /var            ext3    defaults        0       2
/dev/hda9       none            swap    sw              0       0
/dev/hdd        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/hda1       /mnt/windows    ntfs    umask=0222      0       0 

```

Just in case this could come in handy.

PS. The chroot command (I was a root before executing it) didn't work earlier when I tried it. :(

---

### Post by DarkT on 2005-06-16
Hmm ok, that fstab should be helpful if you can get chroot to work. What error did the chroot command give?
 
**Added:** I just went through the steps I outlined above to make sure it all works and for me it does.

**Added Again:** I'm really sorry, just went back a page and saw what you wrote about using chroot. I must have scrolled right past it. 
A.) In the command you gave you weren't running as root, try sudoing the chroot command, I think it makes a difference.
B.)Did you try chrooting the full path, not the relative one (not sure if that makes a difference, worth a try)

---

### Post by dolny on 2005-06-16
Your 'tutorial' was certainly helpful. The Grub showed up but after reboot bash doesn't work,  it gives some error with /var/ (var/log couldn't be found), I also didn't mount /proc/ and home is empty without my /dolny/ directory. I'm going to try to mount /proc/ and all the dirs again.

Anyway all the steps you've given me WORKED now. 

There are some errors that I listed, but I'm going to mount it all again with proc and see if that helps.

I'm really grateful for your help!!! Please check this thread from time to time ;)

Edit: OK atm I'm mounting the stuff again but don't know whatd to do with /proc and that errors in var and no /home/dolny

---

### Post by DarkT on 2005-06-16
Glad I could help :)
Unfortunatly I've no idea why it's not working properly now, maybe the partitions weren't cleanly unmouted and you lost some data or maybe it's just not mounting properly. I've never had that happen to me after restoring grub or lilo so I don't know.

---

### Post by dolny on 2005-06-16
The problem is that I can't do anything to fix that (even though I don't know if I'm able to) because sudo and such doesn't work because of 'bash not found' or smth like that - don't remember now. 

How do I mount /proc ? Do I have to?

---

### Post by themoddingden on 2005-06-16
I had to use the 911 cd I have and edit the boot flages with a hard disk editto then i could get into xp to bkup my stuff then had to low level formatt to be able to install kubuntu again .
i got lucky
if i find the proggy in my 911 cd i'll let you know can't remember it now.
Oh ; by the way xp has to be installed first to get picked up by grub.
xp then kubuntu
or else i don't think it works .

---

### Post by DarkT on 2005-06-16
Ok first, to mount proc you have to ```
mount -t proc none /proc
``` 
(a good place to check these things up is the gentoo handbook, google for something like /proc with site:[www.gentoo.org/doc/en/handbook](www.gentoo.org/doc/en/handbook) on then end, I may not use gentoo any more but it's got **very** good documentation).
 
As for bash not being found, I had a similar problem when I managed to b0rk my system a while back but I never resolved it, had to backup and reinstall. It's probably something to do with your home directory not mounting properly, if you can 
```
export PATH=$PATH:/bin:/usr/bin
``` might work, then if you can ```
sudo passwd root 
``` and give root a password if you haven't already. Once you've done this you should be able to log in as root and work from there.

---

### Post by dolny on 2005-06-16
after export the console echoed nothing, but sudo still doesn't work '-bash command not found'.

Guess I'll have to reinstall all :( :( :( :(

What partitions do I need to reinstall in order to get bash working?
I want to keep as much settings and stuff as I can.

---

### Post by DarkT on 2005-06-16
The export shouldn't echo anything, it should just add /bin /usr/bin to your path which means it should then see bash automatically. If it doesn't then I guess that wan't the problem.

As for re-installing it really depends on what you've set up, and also on the fact that some of those settings may be what's causing the problem... A fresh install is probably better and then copy backup files to that new install but you'll have to cherry pick making sure everythting is ok with those files. 
It may be even better to just reconfigure a new system (barring the configs you have in your home directory and a few from /etc such as network stuff and x.org.conf), I tend to find that's quicker than checking and copying old configs.

Also, /var/cache/apt-get/archives contains the last however many megs you specified for apt to keep after downloading.

Best I can think of at the moment.

**Added** I should probably add that before you try reinstalling it might be worth waiting to see if someone round here knows what the problem is (I'm at a  loss atm).

---

### Post by dolny on 2005-06-19
I reinstalled and it works ok. I have a backup of my /home/

I'm very grateful for your help nonetheless.

---

### Post by Fintan on 2005-06-26
[QUOTE=dolny]I reinstalled and it works ok. I have a backup of my /home/

I'm very grateful for your help nonetheless.[/QUOTE]
 Hi out there,
I just had exactly the same problem. I need winslow for macromedia (flash, dream,etc) applications.
Yesterday something sneaked through my firewall and anti-virus/anti trojan/anti everything setup and crashed winxp. I i had to reinstall winxp and ubuntu to root. I kept my /home and all my data is on a seperate partition anyway.
Everthing else that was discused here in the forum either did not work or was to cumbersome.

My suggestion: Implement a recovery for grub on the install cd. Vector, suse and various other distros do it too. Less agr and time wasted. We can't help it that win crashes, but some of us grudgingly still need it.
I know this has probebly been mentioned a mill times, well one more is not going to hurt;))

But hey, i really think you guys give a lot of effort into helping others, well done.

Cheers
Fintan

---

### Post by miarfeus on 2006-08-05
Dude, you are way too pissed off. I hope you never have children.

---

