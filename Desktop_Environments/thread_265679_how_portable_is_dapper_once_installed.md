---
title: "how portable is dapper once installed?"
date: 2006-09-26
forum: Desktop Environments
---

### Post by delfick on 2006-09-26
hello

i was wondering......(cause one day this question may be helpful, not yet.....but when edgy is released, i may do this) 

basically....i've got one 160GB hardrive, which i've partitioned so that i have 5 partitons.
9.9GB for my windows installation, 30.1GB for my programs (i did this long before i found linux), 10GB for my files, 93.5GB for my games, and now 8.5GB for ubuntu (used to be part of the games partition)

My problem now is that there isn't enough room for ubuntu, so if i download anything, it can't be too big otherwise i run out of room....quite surprisingly :p


SO to the question......basically how hard would it be for me to swap what is in my programs partition with what is in my ubuntu partiton? (my programs only occupy 8.8GB, i don't need most of those programs, and i don't use windows except for games, macromedia and psp nowadays so i could make it less than 8.5GB.

If a simple swap isn't possible, is there a script or program or whatever out there that can identify what programs, libraries, etc i have installed on my linux box and create a list of them, as well as back up all my configurations. SO that all i have to do is wipe my programs drive (and reinstall the programs at a later period), install edgy (or dapper) and then do an apt-get install of the list generated and press a button for the program to put back all my configurations.

Is anything like this possible? how risky would it be? does my question make sense?

thnx for ur help :D

---

### Post by yota on 2006-09-26
Your question definitely make sense, and the good new is that linux is extremely flexible about being relocated.
In fact it could be relocated even to a totally new machine.

The down side is that some handwork and some understanding of the system is absolutely needed; otherwise is really easy to endup in a system that just won't boot. 

Basically, in your case, you have to worry about 2 files:

/boot/grub/menu.lst -> boot loader configuration

/etc/fstab -> system's filesystems table

These two files must be corrected after the switch, because they contains pointers reffering to "old" situation.
Before doing anything else you should understand the syntax of these two files.

Then you can format the target partition (mkfs.ext3), copy files (cp -a), adjust the two files above and finally cross fingers and reboot! (but be sure to have a live-cd at hand, so if a mistake was made you can repair it).

The process can be accomplished in minutes, and has no terrible difficulties, but I would NOT recommend a newbee to jump in without full backups and some study... It's easy to lose everything.
But it can be done!

---

### Post by yota on 2006-09-26
At this link

[http://www.arsgeek.com/?p=564](http://www.arsgeek.com/?p=564)

you can find a way to save your installed package list and restore them after a clean reinstall; this way, plus a backup of /home/* folder, is easier and safer.

---

### Post by delfick on 2006-09-26
Thankyou! :D:D

that looks very promising :D

I'll be sure to bookmark this and come back to it when i go to install edgy :D

thnx again :D

(and one more :D, don't think i have enough :p :D)

---

### Post by delfick on 2006-11-13
k then, i've finally gotten around to doing this :D 
(i do have 2 problems i need help with, but here is the story of what i did first, it might help in solving the problem, (for someone who knows what they're doing anyway :D))

so what i did was delete my e: and make the d: smaller so that now i have a 18GB partition all for linux :D

the first thing i tried, was a clean installation.......after changing the live cd to use vesa instead of that s**t nv driver, and then mucking around with stopping gdm and starting x, i finally got x working.......so then i eventually got it to install onto the new partiton, it took a while because it wouldn't except installing on the new partition (i have no idea why, but i got it installed so it's all good :D))

so then it was installed, yay! i thought..... firstly it took over gfxboot and so my computer was using good old grub (ugly) anywho, then the problems started up again. Firstly the list of what was installed didn't seem to work, because i didn't have everything installed and beryl wouldn't compile for me......(o ye, and the gtk pixmap engine wouldn't install :'( )

also the fact that it took forever for me to get an nvidia driver working, cause the official nvidia driver installer wouldn't work, i eventually installed nvidia-glx (i found a tutorial that explained it, but i can't find it again :p)

anywho, by this stage i gave up with the new installation thing, and tried the copy method. 

now i thought this would have to be done with a live cd, so i booted into the live cd and formated the new partition. Then i realised that i couldn't access my hardrive with the live cd, which annoyed me quite a bit, cause i didn't know how to get to my hardrive. So i rebooted the computer so i could get into my old partiton.

funnily enough, grub didn't work.......so i couldn't boot anything.....

so once again i installed edgy onto the new partiton, and so i was able to use grub again and booted into my old partiton. 

at this point it was late and i had had enough so i went to sleep (this was yesturday) and so this morning i started again. 

first i booted into the old partiton, and from there formatted the new partition and then using "sudo cp -a / /media/sda8" i tried to copy my / contents onto the new partiton.

after about half an hour or so i opened gparted and realised that the used space on sda8 was bigger than the size of the old partiton.....which is when i relalised that it was copying the /media folder, and so was copying over the other partitions.....(i was a little frustrated at this point :p) so i stopped that, and reformated the new partiton again...

now, i don't know how to omit folders from the cp command, so i copied every folder individually, leaving out /proc because it wouldn't work (i looked on the internet to see how it could be copied and found some site saying how to backup and restore, and it said to leave out /proc in the backup, so i left it)

so finally, it was copied over, i then changed /boot/grub/menu.lst and /etc/fstab and booted into the operating system (note that i got confused about these two files, and i beleive my problems are created from them as explained below) 

finally it worked !!!!
infact i'm using it now. and it seems to be exactly the same as the old partiton.
but now to the problems.......

**problem one: /etc/fstab**

when i log into the old partition, it used that partition for / and when i log into the new partiton, it uses that partiton for /

so what's the problem? well the /etc/fstab files are the same for both partitons.

this is the /etc/fstab for the new partition
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8 -- converted during upgrade to edgy
UUID=e57fef6d-4fc6-4132-8b59-3326bcaf0739 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=F0B0700BB06FD69E /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=5C48B62D48B60634 /media/sda5 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda6 -- converted during upgrade to edgy
UUID=9DF95B66B7150DE1 /media/sda6 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda7 -- converted during upgrade to edgy
UUID=00933AC840827310 /media/sda7 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hdc1 -- converted during upgrade to edgy
UUID=cf5e0ebb-5e18-4223-af7f-3bae628c83ec /media/hdc1 ext3 defaults,errors=remount-ro 0 1
# /dev/sda9 -- converted during upgrade to edgy
UUID=9a4c59fa-6363-4fc5-86bb-3ed5a9db1208 none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


/dev/hdc1 /home ext3 nodev,nosuid 0 2
/dev/sda7 /media/sda7 ext3 nodev,nosuid 0 2

```

and this is the /etc/fstab for the old partiton
```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda8 -- converted during upgrade to edgy
UUID=e57fef6d-4fc6-4132-8b59-3326bcaf0739 / ext3 defaults,errors=remount-ro 0 1
# /dev/sda1 -- converted during upgrade to edgy
UUID=F0B0700BB06FD69E /media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda5 -- converted during upgrade to edgy
UUID=5C48B62D48B60634 /media/sda5 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda6 -- converted during upgrade to edgy
UUID=9DF95B66B7150DE1 /media/sda6 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/sda7 -- converted during upgrade to edgy
UUID=00933AC840827310 /media/sda7 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# /dev/hdc1 -- converted during upgrade to edgy
UUID=cf5e0ebb-5e18-4223-af7f-3bae628c83ec /media/hdc1 ext3 defaults,errors=remount-ro 0 1
# /dev/sda9 -- converted during upgrade to edgy
UUID=9a4c59fa-6363-4fc5-86bb-3ed5a9db1208 none swap sw 0 0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0


/dev/hdc1 /home ext3 nodev,nosuid 0 2
/dev/sda8 /media/sda8 ext3 nodev,nosuid 0 2

```

now just to explain some things

sda7 is the old partiton
sda8 is the new partition
hdc1 is a second hardrive, which i'm using as /home

so then, why does the /etc/fstab work for both??
also changing fstab so that it mounts sda8 as / instead of sda7, doesn't work.

and look at the attached screenshot, in the new partiton, it thinks that both sda8 and sda7 are mounted at /

**problem2 : /boot/grub/menu.lst**

i'm confused, quite frankly.

i use this to boot up the old partition 
```
title		Debian GNU/Linux, kernel 2.6.17-10-386
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda7 ro splash quiet vga=791
initrd		/boot/initrd.img-2.6.17-10-386
boot
```

and i use this to boot up the new partion
```
title		Debian GNU/Linux, kernel 2.6.17-10-386
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda8 ro splash quiet vga=791
initrd		/boot/initrd.img-2.6.17-10-386
boot
```

now, using (hd0,6) or (h0,7) both works, and i don't know which one to use.....i also thought it would be (hd0,8 ) because it boots from /dev/sda8 but it doesn't work.....


so can anyone help clarify what is going on please?

thnx :D
(sry for the long post)

---

### Post by delfick on 2006-11-14
so no-one is able to help work out why my computer is mounting two partitons as /  ??

---

### Post by raxxerk on 2006-11-14
Ok, first of all fstab kills my eyes for how is it written in your configuration, i edited your file a little bit:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda8 	/ 		ext3 	defaults,errors=remount-ro 0 1
/dev/hdc1       /media/hdc1 	ext3 	defaults,errors=remount-ro 0 1
/dev/sda9	none 		swap 	sw	  	0 	0	
/dev/hdc1 	/home 		ext3 nodev,nosuid 0 2
/dev/sda7 	/media/sda7 	ext3 nodev,nosuid 0 2

/dev/sda1 	/media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda5       /media/sda5 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda6 	/media/sda6 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda7	/media/sda7 ntfs defaults,nls=utf8,umask=007,gid=46 0 1

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

According to fstab you mount only one partition as root, but you mount twice /dev/hdc1, line 2 and line 4, just comment /dev/hdc1       /media/hdc1 	ext3 	defaults,errors=remount-ro 0 1 and you will be fine, i think. Bye

Edit, I just missed the double line for /dev/sda7 comment or erase /dev/sda7	/media/sda7 ntfs defaults,nls=utf8,umask=007,gid=46 0 1 it was for your previous setup of the partition table(ntfs).

---

### Post by raxxerk on 2006-11-14
Sorry, I was confused about your confusing post, here is a fstab more clean:

```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda8 	/ 		ext3 	defaults,errors=remount-ro 0 1
/dev/sda9	none 		swap 	sw	  	0 	0	
/dev/sda7 	/media/sda7 	ext3 nodev,nosuid 0 2

/dev/sda1 	/media/sda1 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda5       /media/sda5 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda6 	/media/sda6 ntfs defaults,nls=utf8,umask=007,gid=46 0 1

/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

I'm confused about hdc1 mounted as /home? Do you have a separate partition for your home directory?

---

### Post by marcog on 2006-11-14
> **delfick said:**
> **problem2 : /boot/grub/menu.lst**

i'm confused, quite frankly.

i use this to boot up the old partition 
```
title		Debian GNU/Linux, kernel 2.6.17-10-386
root		(hd0,7)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda7 ro splash quiet vga=791
initrd		/boot/initrd.img-2.6.17-10-386
boot
```

and i use this to boot up the new partion
```
title		Debian GNU/Linux, kernel 2.6.17-10-386
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda8 ro splash quiet vga=791
initrd		/boot/initrd.img-2.6.17-10-386
boot
```

now, using (hd0,6) or (h0,7) both works, and i don't know which one to use.....i also thought it would be (hd0,8 ) because it boots from /dev/sda8 but it doesn't work.....


so can anyone help clarify what is going on please?

Looks as though you've made a mistake here. Try replacing it will the following (changes in **bold**):

**Old partition:**
```
title		Debian GNU/Linux, kernel 2.6.17-10-386
root		**(hd0,6)**
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda7 ro splash quiet vga=791
initrd		/boot/initrd.img-2.6.17-10-386
boot
```

**New partition:**
```
title		Debian GNU/Linux, kernel 2.6.17-10-386
root		**(hd0,7)**
kernel		/boot/vmlinuz-2.6.17-10-386 root=/dev/sda8 ro splash quiet vga=791
initrd		/boot/initrd.img-2.6.17-10-386
boot
```

For /etc/fstab:

**Old partition**:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda5       /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda6       /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda7       /               ext3    defaults,errors=remount-ro 0 1
/dev/sda8       /media/sda8     ext3    defaults,errors=remount-ro 0 1
/dev/sda9       none            swap    sw 0 0
/dev/hdc1       /media/hdc1     ext3    defaults,errors=remount-ro 0 1
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

**New partition**:
```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda5       /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda6       /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda7       /media/sda7     ext3    defaults,errors=remount-ro 0 1
/dev/sda8       /               ext3    defaults,errors=remount-ro 0 1
/dev/sda9       none            swap    sw 0 0
/dev/hdc1       /media/hdc1     ext3    defaults,errors=remount-ro 0 1
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
```

Somethings strange with the fstab entries you posted though as they pick up /dev/sda7 as ntfs automatically, but they can't be if you installed ubuntu on that partition. :-/

---

### Post by delfick on 2006-11-14
Thankyou peoples :D
all is good now :D

just to clarify for raxxerk, i have two disks, with 6 partitions on the first, and only one on the second.

the first disk is 160gb disk with a partition for my windows installation, my windows program, my new partition for linux, my windows games, the old partition for linux and swap space (in that order on my hardrive)

my second hardrive i have mounted as /home (though i also want it mounted as /media/hdc1 which is why i have it twice in /etc/fstab

and thnx to marcog, i have my /boot/grub/menu.lst set up properly :D

and just for the hell of it, here is my /etc/fstab (much cleaner now :D thankyou)
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/sda1       /media/sda1     ntfs    defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda5       /media/sda5     ntfs    defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda6       /media/sda6     ntfs    defaults,nls=utf8,umask=007,gid=46 0 1
/dev/sda7       /media/sda7     ext3    defaults,errors=remount-ro 0 1
/dev/sda8       /               ext3    defaults,errors=remount-ro 0 1
/dev/sda9       none            swap    sw 0 0
/dev/hdc1       /media/hdc1     ext3    defaults,errors=remount-ro 0 1
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdc1 	/home 		ext3 nodev,nosuid 	0 	2



and here is a screenshot of gparted, :D  [http://delfick755.googlepages.com/muchbetter.jpg](http://delfick755.googlepages.com/muchbetter.jpg)

---

