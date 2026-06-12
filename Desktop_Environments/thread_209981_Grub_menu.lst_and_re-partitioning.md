---
title: "Grub menu.lst and re-partitioning"
date: 2006-07-06
forum: Desktop Environments
---

### Post by crxyem on 2006-07-06
Well it's time for me to dig a tad bit deeper into my experiences with linux. I feel more confident since I set up my Dell 6000 laptop as a dual boot system with WinXP. Well it is now time to completely ditch XP from my laptop. I'm also in the process of ridding myself of all M$ OS from my 2-desktop systems that act as fileservers and I will be a true *nix convert. So before I screw something up I would like to propose a question to see if I understand everything I've digested in regards to re-partioning and editing grub menu.lst. If I understand this correctly grub interprets hard disk info from the bios so partition 1 on hard disk 1 is hd0,0. 

To start my system as is: (info from qtparted)
sda2  ntfs
sda1  swap
sda3  ext3  /root
sda4  ext3  /home

current menu.lst (truncated to display releavent info)
title		Ubuntu, kernel 2.6.12-10-686 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/sda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-686
savedefault
boot

#other operating systems
title		Microsoft Windows XP Professional
root		(hd0,1)
savedefault
makeactive
chainloader	+1

So my goal is to eliminate sda2 which holds my WinXP partition. 
In doing so, all of my current partitions should move numerically down or am I mistaken in this case ?

what I believe will happen
sda2 ,deleted now free space at the begining of drive
sda1 = sda1 swap
sda3 = sda2 ext3 /root
sda4 = sda3 ext3 /home

If I'm correct then I will need to edit menu.lst to read
title		Ubuntu, kernel 2.6.12-10-686 
root		(hd0,[COLOR="Red"]**1**[/COLOR])
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/sda[COLOR="Red"]**2**[/COLOR] ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-686
savedefault
boot

and then remove the info for the old windows partition

If anyone would sanity check what I believe is what will happen. 
sorry if these seems to be a redundant question but it's my first time 
and I'd rather be certain I know what I'm doing. eventually I will alocate the extra freespace a little bit added to / the remaining to /home

Thanks in Advance
D.

---

### Post by Dr. Nick on 2006-07-06
I cant tell you for sure if the numbers will move down by 1 or not, So I wont even guess at it, maybe someone else knows.

What I am thinking though is that if you simply format the ntfs partition to a linux filesystem (as opposed to deleting the partition totally and making it free space)  that the partiton numbers will not change, but this may make reallocation a bit harder.

I have never really thought about doing this before, Hope you get it figured out.

---

### Post by coffeecat on 2006-07-06
I don't know whether sda3 and sda4 will be renumbered if you delete sda2 (from my experience of a similar thing I once did I think they won't be), but if they are you will need to edit /etc/fstab as well otherwise you'll get either a freeze-up or a kernel panic when you try to boot up. For your setup there will be two lines to edit - the ones referring to /home and /root.

Please post back when you do whatever you do. I'd be interested to know what happens.

 **Edit:** If you are unclear about what to change in fstab post back with the file (it's quite small).

---

### Post by crxyem on 2006-07-06
I almost forgot about editing fstab.
so based on the comments I feel confident I understand whats going t\on. 

thanks I'll update after I've do this.

---

