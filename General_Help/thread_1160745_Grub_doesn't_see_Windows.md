---
title: "Grub doesn't see Windows"
date: 2009-05-15
forum: General Help
---

### Post by mitchewr on 2009-05-15
Hey I am new to ubuntu so please be specific if you give me any directions, haha.   Well I installed ubuntu on my computer a few days ago and eveything works fine.  The only problem is that I had planned to dual boot with Windows, but Grub doesn't see/show any Windows OS to boot into.  I'm not sure if it's something I did in the partitioning or what, but I know that I had two separate partitions. . . 1 for windows FAT 32 and one for Linux ext.3   This is what my menu.list.file looks like

## ## End Default Options ##

title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            60317929-30b6-47eb-92a6-f70520a8f9eb
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=60317929-30b6-47eb-92a6-f70520a8f9eb ro quiet splash
initrd          /boot/initrd.img-2.6.28-11-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid            60317929-30b6-47eb-92a6-f70520a8f9eb
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=60317929-30b6-47eb-92a6-f70520a8f9eb ro  single
initrd          /boot/initrd.img-2.6.28-11-generic

title           Ubuntu 9.04, kernel 2.6.28-3-rt
uuid            60317929-30b6-47eb-92a6-f70520a8f9eb
kernel          /boot/vmlinuz-2.6.28-3-rt root=UUID=60317929-30b6-47eb-92a6-f70520a8f9eb ro quiet splash
initrd          /boot/initrd.img-2.6.28-3-rt
quiet

title           Ubuntu 9.04, kernel 2.6.28-3-rt (recovery mode)
uuid            60317929-30b6-47eb-92a6-f70520a8f9eb
kernel          /boot/vmlinuz-2.6.28-3-rt root=UUID=60317929-30b6-47eb-92a6-f70520a8f9eb ro  single
initrd          /boot/initrd.img-2.6.28-3-rt

title           Ubuntu 9.04, memtest86+
uuid            60317929-30b6-47eb-92a6-f70520a8f9eb
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Now I'm not really sure but shouldn't there be a Windows one in that list somewhere?  
Any help please. . . not that I'm dying to get back into Windows mind you, haha.  I just like having the option I guess.  Also it will help if I know what I'm doing if I install this on any of my parents computers.

---

### Post by gletob on 2009-05-15
Could you please open a terminal and paste in this
```
sudo fdisk -l
```
and Copy and paste the output

---

### Post by reevine on 2009-05-16
which version of windows do you have?

Edit: does your windows partition come first or your ubuntu patition?

---

### Post by mitchewr on 2009-05-16
gletob-- I copied and pasted and here is what it put out. . . 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa9aba9ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2641    21213801    b  W95 FAT32
/dev/sda2            2642        9697    56677320    5  Extended
/dev/sda4            9698        9729      257040   88  Linux plaintext
/dev/sda5            2642        5271    21125443+  83  Linux
/dev/sda6            5272        9697    35551813+  82  Linux swap / Solaris

---

### Post by mitchewr on 2009-05-16
reevine-- I have Windows XP, and I'm not sure which one comes first.  How do you determine that?

---

### Post by reevine on 2009-05-16
> **mitchewr said:**
> reevine-- I have Windows XP, and I'm not sure which one comes first.  How do you determine that?
type in terminal(">" indicated new line of code):

>sudo grub
>geometry (hd0)

let me know what you get when you type that in.

---

### Post by reevine on 2009-05-16
> **mitchewr said:**
> gletob-- I copied and pasted and here is what it put out. . . 

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa9aba9ab

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2641    21213801    b  W95 FAT32
/dev/sda2            2642        9697    56677320    5  Extended
/dev/sda4            9698        9729      257040   88  Linux plaintext
/dev/sda5            2642        5271    21125443+  83  Linux
/dev/sda6            5272        9697    35551813+  82  Linux swap / Solaris
from the look of it the first partition is your windows and you seem to have a couple of other linux systems too correct?

---

### Post by reevine on 2009-05-16
> **mitchewr said:**
> Hey I am new to ubuntu so please be specific if you give me any directions, haha.   Well I installed ubuntu on my computer a few days ago and eveything works fine.  The only problem is that I had planned to dual boot with Windows, but Grub doesn't see/show any Windows OS to boot into.  I'm not sure if it's something I did in the partitioning or what, but I know that I had two separate partitions. . . 1 for windows FAT 32 and one for Linux ext.3   This is what my menu.list.file looks like

## ## End Default Options ##

title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            60317929-30b6-47eb-92a6-f70520a8f9eb
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=60317929-30b6-47eb-92a6-f70520a8f9eb ro quiet splash
initrd          /boot/initrd.img-2.6.28-11-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid            60317929-30b6-47eb-92a6-f70520a8f9eb
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=60317929-30b6-47eb-92a6-f70520a8f9eb ro  single
initrd          /boot/initrd.img-2.6.28-11-generic

title           Ubuntu 9.04, kernel 2.6.28-3-rt
uuid            60317929-30b6-47eb-92a6-f70520a8f9eb
kernel          /boot/vmlinuz-2.6.28-3-rt root=UUID=60317929-30b6-47eb-92a6-f70520a8f9eb ro quiet splash
initrd          /boot/initrd.img-2.6.28-3-rt
quiet

title           Ubuntu 9.04, kernel 2.6.28-3-rt (recovery mode)
uuid            60317929-30b6-47eb-92a6-f70520a8f9eb
kernel          /boot/vmlinuz-2.6.28-3-rt root=UUID=60317929-30b6-47eb-92a6-f70520a8f9eb ro  single
initrd          /boot/initrd.img-2.6.28-3-rt

title           Ubuntu 9.04, memtest86+
uuid            60317929-30b6-47eb-92a6-f70520a8f9eb
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

Now I'm not really sure but shouldn't there be a Windows one in that list somewhere?  
Any help please. . . not that I'm dying to get back into Windows mind you, haha.  I just like having the option I guess.  Also it will help if I know what I'm doing if I install this on any of my parents computers.
you can manualy enter your windows system into your menu.lst file.

heres how in terminal (">" indicates new line of code):

>gksudo gedit /boot/grub/menu.lst

then edit the file as such above the first linux entry:

title		Windows XP
rootnoverify	(hd0,0)
savedefault
chainloader	+1

your entry should then look like this:

## ## End Default Options ##

title		Windows XP
rootnoverify	(hd0,0)
savedefault
chainloader	+1

title           Ubuntu 9.04, kernel 2.6.28-11-generic
uuid            60317929-30b6-47eb-92a6-f70520a8f9eb
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=60317929-30b6-47eb-92a6-f70520a8f9eb ro quiet splash
initrd          /boot/initrd.img-2.6.28-11-generic
quiet

title           Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid            60317929-30b6-47eb-92a6-f70520a8f9eb
kernel          /boot/vmlinuz-2.6.28-11-generic root=UUID=60317929-30b6-47eb-92a6-f70520a8f9eb ro  single
initrd          /boot/initrd.img-2.6.28-11-generic

title           Ubuntu 9.04, kernel 2.6.28-3-rt
uuid            60317929-30b6-47eb-92a6-f70520a8f9eb
kernel          /boot/vmlinuz-2.6.28-3-rt root=UUID=60317929-30b6-47eb-92a6-f70520a8f9eb ro quiet splash
initrd          /boot/initrd.img-2.6.28-3-rt
quiet

title           Ubuntu 9.04, kernel 2.6.28-3-rt (recovery mode)
uuid            60317929-30b6-47eb-92a6-f70520a8f9eb
kernel          /boot/vmlinuz-2.6.28-3-rt root=UUID=60317929-30b6-47eb-92a6-f70520a8f9eb ro  single
initrd          /boot/initrd.img-2.6.28-3-rt

title           Ubuntu 9.04, memtest86+
uuid            60317929-30b6-47eb-92a6-f70520a8f9eb
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST


then save and exit. reboot your computer and select your windows xp from the list. lets me know if it boots.

---

### Post by mitchewr on 2009-05-16
reevine--  here's what i got when i pasted in that code

drive 0x80: C/H/S = 9729/255/63, The number of sectors = 156301488, /dev/sda
   Partition num: 0,  Filesystem type is fat, partition type 0xb
   Partition num: 3,  Filesystem type unknown, partition type 0x88
   Partition num: 4,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 5,  Filesystem type unknown, partition type 0x82

And yes you're correct, there are multiple linux systems.  Stuff like ubuntu recovery, ubuntu safe mode, etc.

---

### Post by reevine on 2009-05-16
> **mitchewr said:**
> reevine--  here's what i got when i pasted in that code

drive 0x80: C/H/S = 9729/255/63, The number of sectors = 156301488, /dev/sda
   Partition num: 0,  Filesystem type is fat, partition type 0xb
   Partition num: 3,  Filesystem type unknown, partition type 0x88
   Partition num: 4,  Filesystem type is ext2fs, partition type 0x83
   Partition num: 5,  Filesystem type unknown, partition type 0x82

And yes you're correct, there are multiple linux systems.  Stuff like ubuntu recovery, ubuntu safe mode, etc.
ok well that clarifies that your windows is the first partition. follow the instructions i gave above and it should work.

---

### Post by mitchewr on 2009-05-16
ok so i entered all that stuff in and now Grub see Windows but when I select it to boot it up it says Starting please wait, but never gets any farther.  It just sits there, and if I press any key then it just goes to a blinking cursor and I end up having to manually restart it.  But at least it's seeing it now, haha.

---

### Post by reevine on 2009-05-16
> **mitchewr said:**
> ok so i entered all that stuff in and now Grub see Windows but when I select it to boot it up it says Starting please wait, but never gets any farther.  It just sits there, and if I press any key then it just goes to a blinking cursor and I end up having to manually restart it.  But at least it's seeing it now, haha.
Lol yep. ok try this go into terminal and type:

>sudo grub
>find /boot/grub/stage1

let me know of the results.

---

### Post by mitchewr on 2009-05-16
All it came up with was (hd0,4)

---

### Post by reevine on 2009-05-16
> **mitchewr said:**
> All it came up with was (hd0,4)
ok that means that GRUB is only being based from one installation.
type in terminal:

>sudo grub
>root (hd0,4)
>setup (hd0)
>quit
>sudo shutdown -h -P now

then try to boot into windows and see if that works.

---

### Post by mitchewr on 2009-05-16
i entered that stuff and reboot it and it is still getting stuck on Starting up. . .

---

### Post by reevine on 2009-05-16
> **mitchewr said:**
> i entered that stuff and reboot it and it is still getting stuck on Starting up. . .
how did you install UbuntU?

---

### Post by mitchewr on 2009-05-16
Off a disk.  I downloaded it from this website and put it in the cd tray and went to work.  If that's what you mean, ha.

---

### Post by reevine on 2009-05-16
ok copy all of your important data that you would like to keep and put it on a flash drive or external hard drive. a cd will work too.

when you have done this go and boot from the Ubuntu CD and when you get to the partition part pick advance partitioning and delete all of the linux partitions and make two partitions one a "ext3" and one a "swap". make your swap about 2GB big. the mount point for your ext3 should be "/". then wait for it to install and let me know if that works.

---

### Post by mitchewr on 2009-05-16
well i don't really have any important data aside from one or two cds on here, but is there a way to save my applications ive downloaded, or any of my settings?  that kind of stuff

---

### Post by reevine on 2009-05-16
> **mitchewr said:**
> well i don't really have any important data aside from one or two cds on here, but is there a way to save my applications ive downloaded, or any of my settings?  that kind of stuff
im not sure how to save applications you've downloaded. someone else might be able to help with that.

Thats about all i can think of to help. i cant think of anything else that you might do with grub to fix it. how long have you waited for windows to boot?

---

### Post by mitchewr on 2009-05-16
oh well thats ok.  Ive only downloaded a couple of games and stuff any ways.  I was just wondering.  Uhm well I didn't wait like 5 or 10 minutes for windows to load, but you know like a couple of minutes probably.  Does it normally take longer when ur dual booting?

---

### Post by reevine on 2009-05-16
> **mitchewr said:**
> oh well thats ok.  Ive only downloaded a couple of games and stuff any ways.  I was just wondering.  Uhm well I didn't wait like 5 or 10 minutes for windows to load, but you know like a couple of minutes probably.  Does it normally take longer when ur dual booting?
no it shouldnt. though i did find one more thing that you might be able to do. i dual boot with 9.04 and Vista. despite how crappy Vista is compared to XP its alot smarter with the booting operations. that makes it easier for ubuntu to boot it. try adding:

makeactive 

in your menu.lst file. put this right under "savedefault" remember to open it by the terminal. this might make a difference. i have heard that some windows cant boot without it.

---

### Post by reevine on 2009-05-16
> makeactive

in your menu.lst file. put this right under "savedefault" remember to open it by the terminal. this might make a difference. i have heard that some windows cant boot without it.

title Windows XP
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1

that is what it should look like. after you are done.

---

### Post by mitchewr on 2009-05-16
well i re-installed ubuntu and re-made all the partitions and everything, but windows still wont boot.  I made the extra change to my menu.list and now (again) grub sees windows but it still gets stuck and Starting up. . . 
It's weird.  Also now when I go to "places"  it's seeing the 12 gigs that I have set aside for Windows ( it used to be 20 but i shrunk it down just now).   It never used to see it before, but again it isn't recognizing it as an OS, you know.   

It looks like I really will be Windows free, after all, haha.

---

### Post by reevine on 2009-05-16
> **mitchewr said:**
> well i re-installed ubuntu and re-made all the partitions and everything, but windows still wont boot.  I made the extra change to my menu.list and now (again) grub sees windows but it still gets stuck and Starting up. . . 
It's weird.  Also now when I go to "places"  it's seeing the 12 gigs that I have set aside for Windows ( it used to be 20 but i shrunk it down just now).   It never used to see it before, but again it isn't recognizing it as an OS, you know.   

It looks like I really will be Windows free, after all, haha.
the only thing i can think of is that there is something wrong with windows. well at least its actually reconizing the windows partition when it didn't before. i hope you get this problem figured out. maybe someone else might be able to figure it out. last thing i can think of might be to reinstall windows.

Edit: try looking up on how to repair windows and repairing the bootloader for windows. then when you do that boot into your live CD and go into your terminal and try: 

>sudo grub
>find /boot/grub/stage1
>root (in these parenthesis put the hard drive that pops up from the previous command. e.g. (hd0,1))
>setup (hard drive selected from previous command but with out the partition. e.g. (hd0))

see if that works after repairing windows MBR and reflashing GRUB. good luck im at the extent of my knowledge on this subject. lol

---

### Post by ladydonna on 2009-05-16
Hi Reevine,  This is ladydonna, form last night. This computer got shut off and I lost the directions you gave me to help with the problerms I asm having. I am new to this forum and don't know how to go back to the posts we had from last night, also I dont know how to personal message you. I would like to try to solve this problem and am ready to start now and work the rest of the day until I get this straightened out. I would appreciate your help. I will be watching this posting here for instructions on how to contact you and greatfully accept your help.  Respectfully, Donna

---

### Post by reevine on 2009-05-16
> **ladydonna said:**
> Hi Reevine,  This is ladydonna, form last night. This computer got shut off and I lost the directions you gave me to help with the problerms I asm having. I am new to this forum and don't know how to go back to the posts we had from last night, also I dont know how to personal message you. I would like to try to solve this problem and am ready to start now and work the rest of the day until I get this straightened out. I would appreciate your help. I will be watching this posting here for instructions on how to contact you and greatfully accept your help.  Respectfully, Donna
hello ladydonna. before we start anything i would like to welcome you to Ubuntu Forums!! 

ok to get back to the posts we were on simply type in your name "ladydonna" in the search and it should show all the threads you have posted on. find the one you created and click on it. then click on "thread tools" at the top of the thread. then click "subscribe to this thread". anytime you want to see that post go to "quick links" at the top of the page and click "subscribed threads" this will show a list of threads that you have subscribed to. click on the one you want and there you go. hopes this helps.

---

