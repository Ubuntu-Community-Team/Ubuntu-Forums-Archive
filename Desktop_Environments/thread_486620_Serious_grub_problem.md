---
title: "Serious grub problem"
date: 2007-06-28
forum: Desktop Environments
---

### Post by asfaq on 2007-06-28
I was playing around with the menu.lst file in boot and i managed to change something in there.. now, everytime i start the computer, it wont give me the options to either load ubuntu or windows.. tried editing the menu.lst file myself and things have become worse now. Now, it doesnt automatically go into linux too! Gives me an error..

could someone please help me fix the menu.lst file please? am completely clueless... My Windows XP is on sda3

fdisk -| gives me this result:

```
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1216     9767488+  83  Linux
/dev/sda2            1217        3648    19535040    b  W95 FAT32
/dev/sda3            3649        4742     8787555    b  W95 FAT32
/dev/sda4   *        4743        4865      987997+  82  Linux swap / Solaris

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        9729    78148161    7  HPFS/NTFS
```

and the menu.lst file looks like this...

```
#title		Windows XP
#root		(hd0,3)
#savedefault
#makeactive
#chainloader	+1
#
title		Linux
root		(hd0,0)
kernel	/vmlinuz root=/dev/hda2 ro

[COLOR="DarkOrange"]other text in the middle[/COLOR]

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=3838b6dd-177d-4be5-8764-6b604c29672f ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=3838b6dd-177d-4be5-8764-6b604c29672f ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3838b6dd-177d-4be5-8764-6b604c29672f ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3838b6dd-177d-4be5-8764-6b604c29672f ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

```

i'd really really appreciate it if someone could help me fix this!

---

### Post by alienexplorers on 2007-06-28
Try inserting your live cd and boot it.
Then open terminal and type in:
> sudo grub
Then type in:
> find /boot/grub/stage1
you will get an output like (hd #,@) where # is your drive number and @ is your partition number.
Enter:
> root (hd#,@)
setup (hd#)
make sure in the setup line you leave off the partition number.
quit grub editor
reboot

---

### Post by asfaq on 2007-06-28
i dont have the live cd with me.. moreover.. i want to be able to access my win xp partition too from grub.. any clues.. the linux partition resides on sda1 and win xp resides on sda3

---

### Post by logos34 on 2007-06-28
wow, i've seen some really messed up menu.lst's in the last couple of days!

First off, you've hashed out (#) the windows xp entry in menu.lst, so it won't even appear on the grub menu screen.  Secondly, the wrong partition is flagged bootable (*) on the fdisk printout.  You need to use a gparted live cd or the the Gnome Partition Editor on the ubuntu live cd to fix that.  Right click on swap and get rid of that asterisk (*).  Then add 'boot' flag to sda1.

Looks like your winxp partition is on the other hard disk, sdb1.  (Maybe the fat32's sda2 and sda3 are data partitions?).  If so, sdb1 needs a 'boot ' flag too. 

Take out this:

> #title		Windows XP
#root		(hd0,3)
#savedefault
#makeactive
#chainloader	+1
#
title		Linux
root		(hd0,0)
kernel	/vmlinuz root=/dev/hda2 ro

Your kernel entries look fine at 'root (hd0,0)' -- that's sda1

Elsewhere on menu.lst, set:

**default  saved**

**timeout  10**

**#hiddenmenu**


Put this at the bottom:

> title		Windows XP
root		(hd1,0)
map            (hd0) (hd1)
map            (hd1) (hd0)
savedefault
makeactive
chainloader	+1

/boot/grub/menu.lst should look like this:

> (hd0) /dev/sda
(hd1) /dev/sdb

---

### Post by asfaq on 2007-06-29
@logos34 : the reason i actually hashed out the XP entry is cuz i wanted to load into Ubuntu all the time.. there are just sometimes that i need to get into xp to get some things done.. thats where i wanted to be able to press esc on the grub splash screen and choose win xp from there..

i'll try this out right now and let u know how it went!

---

### Post by Canis familiaris on 2007-06-29
If you do not want to see the menu except to press esc then do the following change in red
Just change the timeout to 0
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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
**[COLOR="Red"]timeout		0[/COLOR]**

...
```

---

### Post by asfaq on 2007-06-29
@Anurag_panda: thanks for the tip mate! there is loads of learning happening here for me! :) appreciate it

@logos34 : here is the menu'lst file after the changes you recommended..

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default	saved	10

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# kopt=root=UUID=3838b6dd-177d-4be5-8764-6b604c29672f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=3838b6dd-177d-4be5-8764-6b604c29672f ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=3838b6dd-177d-4be5-8764-6b604c29672f ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3838b6dd-177d-4be5-8764-6b604c29672f ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3838b6dd-177d-4be5-8764-6b604c29672f ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1

gonna boot now! hope this works!

---------------------------------------------

Update: Tried booting.. I can boot into Ubuntu just fine now but Win XP still gives me an error saying:

Error 21: Selected disk does not exist

This i think i because my disk partions for xp are mapped incorrectly in grub.. i could be wrong though.. thanks for the help guys! u all hav been fab.. having said that only this one last little niggle needs to be fixed and am hoping for more help.. 

Asfaq.

---

### Post by logos34 on 2007-06-29
> default saved [COLOR="Red"]10[/COLOR]

Take out the '10'.  Should be:

**default saved**


> Update: Tried booting.. I can boot into Ubuntu just fine now but Win XP still gives me an error saying:

Error 21: Selected disk does not exist

This i think i because my disk partions for xp are mapped incorrectly in grub.. i could be wrong though.. 

Did you remember to edit /boot/grub/device.map, as I said at the end of Post #4?

> (hd0) /dev/sda
(hd1) /dev/sdb

---

### Post by asfaq on 2007-06-29
> **logos34 said:**
> Take out the '10'.  Should be:

**default saved**


ok, done that now..

> **logos34 said:**
> Did you remember to edit /boot/grub/device.map, as I said at the end of Post #4?

To be really honest, i didnt know where to look for it.. it wasnt in the menu.lst file.. sorry about that.. will try again :)

thanks for all the help man! appreciate it :)

******************************************************

Update:

Still no joy.. still get Error 21: Selected disk does not exist

right now my menu.lst file looks like this:

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
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default	saved	

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

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
# kopt=root=UUID=3838b6dd-177d-4be5-8764-6b604c29672f ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=3838b6dd-177d-4be5-8764-6b604c29672f ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=3838b6dd-177d-4be5-8764-6b604c29672f ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3838b6dd-177d-4be5-8764-6b604c29672f ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=3838b6dd-177d-4be5-8764-6b604c29672f ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

title Windows XP
root (hd1,0)
map (hd0) (hd1)
map (hd1) (hd0)
savedefault
makeactive
chainloader +1
```

and the device.map file looks thus:

```
(hd0) /dev/sda
(hd1) /dev/sdb
```

---

### Post by logos34 on 2007-06-29
> map (hd0)    (hd1)
map (hd1)    (hd0)

asfaq,

There may be a spacing typo in that windows entry for menu.lst (see above box).  It's hard to tell though--in your last post it LOOKS as though there's an extra space between the parentheses where there should only be ONE SPACE, but when I copy 'n paste it there's only one space.  Go back to the menu.lst and double check that--even a tiny error on the 'map' lines will mess it up (it's happened to me once before).  

If that doesn't work, then  windows XP must be on sda3, the fat32 partition, which means you purposely installed it on that filesystem rather than NTFS.  I just assumed you were mistaken, and you never corrected me or explained what those two fat32's were.  Maybe you installed xp on fat32 so you could write to it frm linux, I don't know.  If that's the case then try this for the windows entry:

> title Windows XP
root [COLOR="Blue"](hd0,2)[/COLOR]
savedefault
makeactive
chainloader +1

(hd0,2) points to [COLOR="Blue"]sda3[/COLOR], the other fat32 partition.

Or if it's on sda2, use (hd0,1).

---

### Post by asfaq on 2007-07-02
hi.. sorry for the incredibly late reply.. was out over the weekend!

Yes, i have installed XP on sda3 and it is a FAT32 drive for the very reasons u specify in your post above. I mentioned the same in my first post and assumed you had that piece of info already. My bad.

Will change the entry right away and see how it goes.. wish me luck!

---

### Post by logos34 on 2007-07-02
> I mentioned the same in my first post and assumed you had that piece of info already. My bad.

All you said was you installed xp on sda3, and looking at your fdisk I thought you must have been mistaken.  Most people install win xp on ntfs and format only the data partition fat32.  In fact win xp (the system files on C: at least) is better off on ntfs filesystem (fragmentation issues, etc), and fat32 is not even really necessary anymore since there is **fs-driver** for windows (read + write to linux ext3) and **ntfs-3g** for linux (write to ntfs).  Fat32 is also a problem because of 4 GB file size limit (which rules out large backups and images, multimedia files, etc).  Just some things to consider.

Good luck.

---

### Post by asfaq on 2007-07-02
> **logos34 said:**
> Fat32 is also a problem because of 4 GB file size limit (which rules out large backups and images, multimedia files, etc).  Just some things to consider.

I agree with everything u have to say. Its just that I use windows only rarely, if ever. I dont want to add too many applications to this linux box of mine cuz it runs on hardware that was manufactured in the stone-age :)

I am writing this entry from my windows partition right now.. so many thanks there.. I changed the menu,lst entry to (hd0,1) which means that XP is installed on sda2 and not sda3 as i previosuly mentioned.. sorry about that.

Thank you very much for the extended support! Appreciate it greatly.

Yours sincerely.

Asfaq.

---

### Post by logos34 on 2007-07-02
> I dont want to add too many applications to this linux box of mine cuz it runs on hardware that was manufactured in the stone-age

ha! hey, you don't know what stone-age is...my last computer was so old that when I was shopping for parts for my new pc I thoight seriously of donating it to a science museum!

> I am writing this entry from my windows partition right now.. so many thanks there.. I changed the menu,lst entry to (hd0,1) which means that XP is installed on sda2 and not sda3 as i previosuly mentioned.. sorry about that.

Ok, glad you can boot into everything now.  Have fun!

---

### Post by asfaq on 2007-07-02
many thanks again :)

Asfaq

---

