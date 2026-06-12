---
title: "i cant start ubuntu................"
date: 2006-08-09
forum: Desktop Environments
---

### Post by L_o_N_e_R on 2006-08-09
the GRUB bootloader wont run.... which means i cant run ubuntu...

it keeps on starting on winxp.....


is there a way to fix this?

---

### Post by scxtt on 2006-08-09
do you have a live CD? -- running **sudo grub-install [device]** should set grub up on [device] ...

if you do have one, check out **man grub-install** for some more info one it ...

---

### Post by L_o_N_e_R on 2006-08-09
um ok i run the cd and type that in the terminal?

---

### Post by scxtt on 2006-08-09
yes, the commands in bold can be run in a terminal ... i don't know the setup of your HDDs, so i do advise the **man grub-install** reading first ...

---

### Post by L_o_N_e_R on 2006-08-09
what device do i run it on?

---

### Post by L_o_N_e_R on 2006-08-09
where do i put it?

/dev/hda1
/dev/hda2
/dev/hda3
or
/dev/hda4
?

---

### Post by scxtt on 2006-08-09
i'd advise **/dev/hda1** ... it might also just want **/dev/hda** ...

---

### Post by L_o_N_e_R on 2006-08-09
so the command would be sudo grub-install /dev/hda1
?

---

### Post by L_o_N_e_R on 2006-08-09
could not find device for /boot: not found or not a block device

---

### Post by scxtt on 2006-08-09
what did you do exactly? -- assuming /dev/hda1 is you root directory (and you have a /boot directory located there, which is key, having your kernet/initrd in a /boot dir) - a simple **sudo grub-install /dev/hda** should work ...

but if /boot is on /dev/hda3 (for example) you might need to do:
[indent]**sudo grub-install --root-directory=/dev/hda3/boot /dev/hda**[/indent]
i'm not sure, never had to do it that way ...

---

### Post by L_o_N_e_R on 2006-08-09
um how do i check where my boot is?.......

---

### Post by scxtt on 2006-08-09
when you're in the LiveCD you should be able to mount you disks ... so try mounting each partition and see which one has /boot on it ...

---

### Post by L_o_N_e_R on 2006-08-09
and to mount my disks i have to.....



Edit: i went to the partitioner editor and this is what it says

/dev/hda1 fat32 flags:boot lba
/dev/hda2 fat32 hidden lba
/dev/hda3 linux swap
/dev/hda4 ext3

---

### Post by L_o_N_e_R on 2006-08-09
bump

---

### Post by scxtt on 2006-08-09
looks like /dev/hda4 contains the /boot directory - since it's the only one formatted for a Linux OS ...

and i didn't know you had no idea how to mount a disk - never know what level of 'compentency' you're dealing with here (and we're not in the "absolute beginner" section) ...

---

### Post by L_o_N_e_R on 2006-08-09
heh thnx man :)

ill post stuff in the right section now :p

---

### Post by scxtt on 2006-08-09
no problemo - we all start somewhere :) ...

let me know if it works, cause that's def. a handy thing to be able to do ...

---

### Post by L_o_N_e_R on 2006-08-09
-.- same error............................

---

### Post by L_o_N_e_R on 2006-08-09
reinstall FTW?

---

### Post by scxtt on 2006-08-09
ok, let's make sure /boot even exists on /dev/hda4 ...

run these commands from the live CD:

1. sudo mkdir /media/hda4
2. sudo mount /dev/hda4 /media/hda4
3. ls -l /media/hda4

and post the results of step #3 ...

---

### Post by L_o_N_e_R on 2006-08-09
cant even go to step 3 -.-

error message on step 2: mount cant find /dev/hda4/media/hda4 or /etc/mtab

ill retry

---

### Post by scxtt on 2006-08-09
there are spaces b/t /dev/hda4 and /media/hda4 ...

in other words, a typo ...

---

### Post by L_o_N_e_R on 2006-08-09
no spaces

heres what i type:sudo mount /dev/hda4/media/hda4

---

### Post by maniacmusician on 2006-08-09
he means there are *supposed* to be spaces. this is what you should type: sudo mount /dev/hda4 /media/hda4

and then go on to do what he said in step 3.

---

### Post by scxtt on 2006-08-09
yeah, i did say "there **ARE** spaces b/t /dev/hda4 and /media/hda4 ..." as in there are SUPPOSED to be ... :)

---

### Post by L_o_N_e_R on 2006-08-09
total 128........ way too many stuff im on a diff comp :p 


all have root in them so we found it?


edit nvm here it is

total 128
drwxr-xr-x   2 root root  4096 2006-08-09 17:57 bin
drwxr-xr-x   3 root root  4096 2006-08-09 18:12 boot
lrwxrwxrwx   1 root root    11 2006-08-08 21:56 cdrom -> media/cdrom
drwxr-xr-x   4 root root  8192 2006-05-31 00:55 dev
drwxr-xr-x 106 root root  4096 2006-08-10 02:03 etc
drwxr-xr-x   3 root root  4096 2006-08-08 22:08 home
drwxr-xr-x   2 root root  4096 2006-05-31 00:49 initrd
lrwxrwxrwx   1 root root    29 2006-08-09 18:13 initrd.img -> boot/initrd.img-2.6.15-26-386
lrwxrwxrwx   1 root root    29 2006-08-08 21:57 initrd.img.old -> boot/initrd.img-2.6.15-23-386
drwxr-xr-x  19 root root  4096 2006-08-08 22:13 lib
drwxr-xr-x   2 root root 49152 2006-08-08 21:56 lost+found
drwxr-xr-x   5 root root  4096 2006-05-31 00:49 media
drwxr-xr-x   2 root root  4096 2006-05-22 14:00 mnt
drwxr-xr-x   3 root root  4096 2006-08-09 23:34 opt
drwxr-xr-x   2 root root  4096 2006-05-22 14:00 proc
drwxr-xr-x   7 root root  4096 2006-08-09 17:56 root
drwxr-xr-x   2 root root  8192 2006-08-09 18:06 sbin
drwxr-xr-x   2 root root  4096 2006-05-31 00:49 srv
drwxr-xr-x   2 root root  4096 2006-05-21 18:46 sys
drwxrwxrwt   6 root root  4096 2006-08-10 02:02 tmp
drwxr-xr-x  11 root root  4096 2006-05-31 00:51 usr
drwxr-xr-x  14 root root  4096 2006-05-31 01:02 var
lrwxrwxrwx   1 root root    26 2006-08-09 18:13 vmlinuz -> boot/vmlinuz-2.6.15-26-386
lrwxrwxrwx   1 root root    26 2006-08-08 21:57 vmlinuz.old -> boot/vmlinuz-2.6.15-23-386

---

### Post by scxtt on 2006-08-09
it's there in red ...

[font=courier]```
total 128
drwxr-xr-x 2 root root 4096 2006-08-09 17:57 bin
[color=red]drwxr-xr-x 3 root root 4096 2006-08-09 18:12 boot[/color]
lrwxrwxrwx 1 root root 11 2006-08-08 21:56 cdrom -> media/cdrom
drwxr-xr-x 4 root root 8192 2006-05-31 00:55 dev
drwxr-xr-x 106 root root 4096 2006-08-10 02:03 etc
drwxr-xr-x 3 root root 4096 2006-08-08 22:08 home
drwxr-xr-x 2 root root 4096 2006-05-31 00:49 initrd
lrwxrwxrwx 1 root root 29 2006-08-09 18:13 initrd.img -> boot/initrd.img-2.6.15-26-386
lrwxrwxrwx 1 root root 29 2006-08-08 21:57 initrd.img.old -> boot/initrd.img-2.6.15-23-386
drwxr-xr-x 19 root root 4096 2006-08-08 22:13 lib
drwxr-xr-x 2 root root 49152 2006-08-08 21:56 lost+found
drwxr-xr-x 5 root root 4096 2006-05-31 00:49 media
drwxr-xr-x 2 root root 4096 2006-05-22 14:00 mnt
drwxr-xr-x 3 root root 4096 2006-08-09 23:34 opt
drwxr-xr-x 2 root root 4096 2006-05-22 14:00 proc
drwxr-xr-x 7 root root 4096 2006-08-09 17:56 root
drwxr-xr-x 2 root root 8192 2006-08-09 18:06 sbin
drwxr-xr-x 2 root root 4096 2006-05-31 00:49 srv
drwxr-xr-x 2 root root 4096 2006-05-21 18:46 sys
drwxrwxrwt 6 root root 4096 2006-08-10 02:02 tmp
drwxr-xr-x 11 root root 4096 2006-05-31 00:51 usr
drwxr-xr-x 14 root root 4096 2006-05-31 01:02 var
lrwxrwxrwx 1 root root 26 2006-08-09 18:13 vmlinuz -> boot/vmlinuz-2.6.15-26-386
lrwxrwxrwx 1 root root 26 2006-08-08 21:57 vmlinuz.old -> boot/vmlinuz-2.6.15-23-386
```[/font]

---

### Post by L_o_N_e_R on 2006-08-09
and so what do i do?

edit tried sudo gru-install /dev/hda4 

same error....

---

### Post by scxtt on 2006-08-09
try:

**sudo grub-install --root-directory=/dev/hda4/boot /dev/hda**

i'm not sure what **--root-directory** expects (maybe /media/hda4/boot) ... the man page just says **--root-directory=DIR** ... i'd try different combos involving hda4/boot ...

check this out too: [http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html](http://www.gnu.org/software/grub/manual/html_node/Installing-GRUB-using-grub_002dinstall.html)

---

### Post by L_o_N_e_R on 2006-08-09
tried yours 

error: mkdir : cannot creat directory '/dev/hda4/boot/boot' : not a directory...


should i ommit the boot part?

---

### Post by maniacmusician on 2006-08-10
oops i made a mistake. disregard my post.

---

### Post by scxtt on 2006-08-10
yeah, try removing the end **boot**, if the post above gives you an error as well ...

---

### Post by L_o_N_e_R on 2006-08-10
same error


input sudo grub-install --root-directory=/dev/hda4 /dev/hda

---

### Post by scxtt on 2006-08-10
**sudo grub-install --root-directory=/boot /dev/hda**

and if it doesn't work:

**sudo grub-install --root-directory=/boot /dev/hda4**

seems to me that a simple:

**grub-install /dev/hda**

should work ...

---

### Post by L_o_N_e_R on 2006-08-10
both give same error 

cant find device for /boot/boot: not found or not a block device

---

### Post by scxtt on 2006-08-10
i don't get the 2x boot thing, but it looks like --root-directory might only pertain to if you had a specific /boot partition, which you don't ...

have you tried **sudo grub-install /dev/hda** -or - **sudo grub-install /dev/hda4**?

---

### Post by L_o_N_e_R on 2006-08-10
still cant find boot......

---

### Post by L_o_N_e_R on 2006-08-10
i might be tempted to reinstall if i dont get this right......

---

### Post by scxtt on 2006-08-10
honestly, i'm surprised you're having this specific problem, especially ex post facto after installing ubuntu ... 99.9% of the time when it comes to grub, it will recognize your existing XP partition and install grub when/where necessary and present you w/ the appropriate grub menu ... your problems seem more "i installed windows" more than "i installed ubuntu" ... maybe it's some weird anomaly than anything else ...

---

### Post by hadian on 2006-08-10
i think first you should do a chroot command and then run your command. see here: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
so, if the you have mounted the partition ubuntu installed on it first do a chroot to the /boot of that partition and then run grub-install command.

---

