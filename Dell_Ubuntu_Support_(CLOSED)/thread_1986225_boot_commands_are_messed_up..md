---
title: "boot commands are messed up."
date: 2012-05-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by seansunner on 2012-05-24
im stuck in boot screen. i got a dell with ubuntu 10 on it .i think my commands before booting are wrong. it says

recordfail
insmod part_msdos
insmod ext 2
set root='(hd0,msdos3)'
seach --no-floppy --fs-uuid --set e699c4a8-27bd-4201-920b-777416c20/934
linux /boot/vmlinuz-2.6.35-32-generic root=uuid=e699c4a8-27bd-4201-9\20b-777416c20934 ro ?? quiet splash
initrd /boot/initrd.img-2.6.35-32-generic

---

### Post by wilee-nilee on 2012-05-24
> **seansunner said:**
> im stuck in boot screen. i got a dell with ubuntu 10 on it .i think my commands before booting are wrong. it says

recordfail
insmod part_msdos
insmod ext 2
set root='(hd0,msdos3)'
seach --no-floppy --fs-uuid --set e699c4a8-27bd-4201-920b-777416c20/934
linux /boot/vmlinuz-2.6.35-32-generic root=uuid=e699c4a8-27bd-4201-9\20b-777416c20934 ro ?? quiet splash
initrd /boot/initrd.img-2.6.35-32-generic


That can all be rewritten if wrong with a update-grub in the terminal at the desktop.
Or modification of the grub.cfg, correctly using    	 	 	 	 	 	   [FONT=Verdana, sans-serif][SIZE=1]gksudo gedit  /etc/default/grub[/SIZE][/FONT]
  
What is the actual goal here?

---

### Post by seansunner on 2012-05-24
im trying to get my computer to work again, its all jacked up.

how would i upgrade grub.
im so confused

---

### Post by wilee-nilee on 2012-05-24
> **seansunner said:**
> im trying to get my computer to work again, its all jacked up.

how would i upgrade grub.
im so confused

It happens, in the terminal on the ubuntu install run.

```
sudo update-grub
```So I am hesitant to say more really as to much detail is missing here to really be of help.

If you can share more that would be helpful, if the update does not work.

We have a script easily run from a app, or a copy and paste of commands that will debug your bootset up generally with being read by us or you, and the correct commands run then.

If your not even able to boot in, is important info.

---

### Post by seansunner on 2012-05-24
i cant even boot in...... i put in "sudo update grub,and it says the same thing.... i think i deleted the directorys and i tryed to reboot and i got stuck on the recovery grub screen..they all come up with 

mounting /dev on root/dev failed: no such file or directory
mounting /sys/on /root/sys failed:no such.....
mounting /proc on /root/proc failed:no such .....
target filesystem doesnt have requested /sbin/init.
no init found. try passing init=bootarg



busybox v1.15.3 ubuntu 1:1.15.3-1ubuntu5 biult in shell-ash

and then  its in


(initrtamfs)


if that is what what u mean by more info?

---

### Post by wilee-nilee on 2012-05-24
Okay lets  do this, from a live ubuntu cd booted, run these three commands. Then look in the home for a results.txt, open it and copy and paste all the text to a reply.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
``` ```
chmod a+x bootinfoscript
``````
sudo bash bootinfoscript
```

---

### Post by wilee-nilee on 2012-05-24
Any command I post as well is a copy and paste if you want, these tend to be case sensitive.

So I always copy and paste myself makes it easier. :)

---

### Post by seansunner on 2012-05-24
it still says 'could not find kernel image...


would that mean my kernel image file is missing??

the cd boots for a sec then it says



stdin: error 0
/init: line 7: cant open /dev/sdb: no medium found
/init: line 7: cant open /dev/sdb: no medium found
chroot: cant execute '/usr/lib/user-setup/user-setup-apply': input/output error
/user/sbin/locale-gen: line 86: /bin/ls: input/output error
/user/sbin/make-ssl-cert: line 33: /bin/hostname: input/output error
/user/sbin/make-ssl-cert: line 34: /bin/hostname: input/output error
grep: /root/cdrom/preseed/ubuntu.seed:no such file or directory
ln: root/usr/lib/update-notifier/apt-check:no such file or directory
Traceback: (most recent call last)
file "/usr/bin/fontconfig-voodoo", line 101, in module main
file "/usr/bin/fontconfig-voodoo', line 56, in main fc = fontconfig.fontconfighack
file "/....something something something.....
i0error
using cd-rom mount point /cdrom/
identifying.. "long number"
scanning disk for index files
found 0 package indexes, 0 source indexes, 0 translation indexes and 0 signatures
E:unable to locate any package files, perhaps this is not a debian disc or wrong archertecure
chroot: cant execute rm
init failed to spawn hostname.....
init failed to spawn hwclock.....
init failed to spawn mountall 
init failed to spawn mountall post-stop

---

### Post by seansunner on 2012-05-24
i cant copy and paste, im on another computer cuz mine is broken

---

### Post by wilee-nilee on 2012-05-24
> **seansunner said:**
> i cant copy and paste, im on another computer cuz mine is broken

So short of a manual boot of grub you will need to get this script posted if possible, and also maybe just try this app which will run basic repair and generate the script to a HTTP address.

A manual boot is a geek area, I don't really have the patience to go there just to be honest. :)

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

If you want help in fixing this, if it can be, you have to get creative. If you have a usb/flash/ or hard drive, or cd that will transfer stuff from the broken computer to the device you're posting with use it to post the stuff run on the broke computer.

Try the recommended repair on the boot-repair and post the generated script if that does not work. :)

---

