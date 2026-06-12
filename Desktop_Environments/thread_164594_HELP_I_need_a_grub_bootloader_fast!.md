---
title: "HELP** I need a grub bootloader fast!"
date: 2006-04-23
forum: Desktop Environments
---

### Post by n00bWillingToLearn on 2006-04-23
edit: Problem solved via miraculous recovery no more help needed. :)

I just installed pcLinux and I need to boot into windows and at boot I am not seeing the Grub bootloader I don't care about fixing it right now I know that my Windows partition is fine and I need to boot into it NOW. Is there for instance grub on a CD that I can use? The machine does not have a floppy drive so I can not use any of the bootloaders on a floppy that I have seen before ](*,). please help!

---

### Post by r4ik on 2006-04-23
Here is a read hope it helps,

[http://www.ubuntuforums.org/showthread.php?t=76652&highlight=howto+restore+Grub](http://www.ubuntuforums.org/showthread.php?t=76652&highlight=howto+restore+Grub)

Good luck.

---

### Post by n00bWillingToLearn on 2006-04-23
Whell I don't know what happend but there is now a grub bootloader? My dad started up his machine after trying a few rescue cds but never actually making any changes and his machine is up and running (for now?) I will take some time later to figure out his problem ( if he ever had one ) with grub but crisis has been overted for now. It would still be interesting to put grub on a cd just to see what it takes to do it but I don't really need any help for now.

---

### Post by Herman on 2006-04-23
Hello, nOObWillingToLearn, The easiest way to boot Windows is from a CD is to use GAG Boot Manager on '[System Rescue CD]("http://www.sysresccd.org/Main_Page")', or [make your own GAG CD]("http://www.users.bigpond.net.au/hermanzone/p12.htm"). Then even if you don't need it anymore at the moment, you will be able to find it and use it some day when you have that problem again.
I agree with you that it would be interesting to try to make a GRUB CD too though. I have made GRUB floppy disks before, and those seem to be relatively common, but I haven't heard of people making GRUB CD's and I don't know why not. 
I just did a google search and found [this interesting article]("http://www.gnu.org/software/grub/manual/html_node/Making-a-GRUB-bootable-CD-ROM.html"), it looks like it's in the GRUB manual. Maybe I'll give it a try too, just for fun and see if I can do it.   A CD-RW would be good for that, then if it doesn't turn out we can just erase it and use it again and not waste money on CDs.
Have fun, Regards, Herman. :D

---

### Post by Herman on 2006-04-23
Well, nOObWillingToLearn, I have been having some fun and I have just made my first successful GRUB CD, thanks to your query. It took me several attemps before I got it right.
Here's how I finally did it.   EDITED with corrections 13/05/06

1)   stage2_eltorito can be found in Ubuntu in /lib/grub/i386-pc directory.
I copied that to my home directory like this:
```
~$  cp /lib/grub/i386-pc/stage2_eltorito .

``` Note for new users, there is a space after the word eltorito and the fullstop (or period in American/Canadian English) is after the space. That is a Linux abbreviation for /home/username directory. Be sure to include the space and fullstop in your command, those are more important than they may look. The same applies to the next command.

2) I copied my /boot/grub/menu.lst and pasted it in my /home/herman directory,
```
~$ cp /boot/grub/menu.lst .
``` 
3) I opened the new copy of menu.lst with 'gedit', and deleted the commands 'savedefault' from my Ubuntu boot entries.
I altered the entry for Windows from 'root' to 'rootnoverify', deleted the command 'savedefault', and added the command 'boot' at the bottom, and saved and closed the text file.


4) Then I applied the following terminal commands:
```
~$ mkdir iso
~$ mkdir -p iso/boot/grub
~$ cp menu.lst iso/boot/grub/
~$ cp stage2_eltorito iso/boot/grub/
~$ cp /boot/grub/DigitalAnGeL.xpm.gz iso/boot/grub/ 
``` The last command there would not be needed for most people, it's just because I have added a fancy  'splashimage', most people can skip that one.

5) And here's the final code from the Grub manual: ```
~$mkisofs -R -b boot/grub/stage2_eltorito -no-emul-boot \
 -boot-load-size 4 -boot-info-table -o grub.iso iso
``` Here's what it said back to me:> INFO:   UTF-8 character encoding detected by locale settings.
        Assuming UTF-8 encoded filenames on source filesystem,
        use -input-charset to override.
Size of boot image is 4 sectors -> No emulation
Total translation table size: 2048
Total rockridge attributes bytes: 1258
Total directory bytes: 4096
Path table size(bytes): 34
Max brk space used 21000
345 extents written (0 MB) 6) After that I just put my CD-RW in the drive, went through my /home/herman directory, clicked on the new .iso and clicked 'write to disk'. 
7) I have tested my new GRUB boot CD-RW disk and it boots Ubuntu or Windows in my computer just fine!
This was interesting and fun, maybe it will be useful to somebody. Regards, Herman :D

---

