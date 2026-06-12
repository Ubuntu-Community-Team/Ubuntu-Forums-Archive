---
title: "How to boot among different hard drives?"
date: 2009-05-23
forum: General Help
---

### Post by angus1000 on 2009-05-23
Recently I configured one of my SATA drives to dual boot Ubuntu and Windows 7. I simply choose which OS to boot into from the Ubuntu boot menu. This seems to be working fine.

I have another HDD with Vista installed on it.

Right now I physically disconnect one drive and reconnect the other to switch between Ubuntu/Windows 7 drive and the Vista drive. Ideally I'd like to have all drives powered and select one of the three OS from the Ubuntu boot menu.

With all drives connected right now I'm not sure which drive my PC will select since both have active bootloaders. I've haven't tried this for fear of completely hosing my Vista drive. 

I'm not sure how to proceed. What do I have to do to get all drives & OS's to appear on a single boot menu? I couldn't find anything on the web that addressed booting in this fashion.

Come to think of it, is it just a matter of editing my menu.lst file (Ubuntu)....not sure how to map the other drive over?

Any help will be appreciated.

Thanks,
Angus

---

### Post by lindsay7 on 2009-05-23
See this post.

[http://ubuntuforums.org/showthread.php?t=1167841](http://ubuntuforums.org/showthread.php?t=1167841)

---

### Post by Legace on 2009-05-23
1) Plug in both drives
2) Make sure your drive, on which Ubuntu is, is the "Master" drive (set this from your BIOS).
3) Now you should be able to boot into Ubuntu.

Once you're done, post the contents of **/boot/grub/menu.lst** and also the output of **blkid** (in Terminal).

---

### Post by angus1000 on 2009-05-30
Legace,

Here is the info I think you want from me:

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        a8a201fa-2e59-4f88-8cc3-9f5bfb4e6d4e
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a8a201fa-2e59-4f88-8cc3-9f5bfb4e6d4e ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        a8a201fa-2e59-4f88-8cc3-9f5bfb4e6d4e
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=a8a201fa-2e59-4f88-8cc3-9f5bfb4e6d4e ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        a8a201fa-2e59-4f88-8cc3-9f5bfb4e6d4e
kernel        /boot/memtest86+.bin
quiet

title windows 7 beta (Loader)
root (hd0,1)
savedefault
makeactive
chainloader +1

/dev/sda1: UUID="a8a201fa-2e59-4f88-8cc3-9f5bfb4e6d4e" TYPE="ext3" 
/dev/sda5: UUID="fcd42f60-a78d-4b60-a139-32b792fc79d7" TYPE="swap" 

I have configured my BIOS boot order to select the Linux disk before the Vista disk.

So, right now I've got 1 SATA HDD which can dual boot Ubuntu and Windows 7. My other SATA HDD boots Vista only. I want to be able to power up my PC and choose the OS to boot.

BTW, with both drives plugged in I ran gparted just to get the partition information. I don't think that gparted was able to see my Vista drive.


Plet let me know how to proceed. Thanks for the info.

-Angus

---

### Post by angus1000 on 2009-05-30
Best I can tell all I need to do is add this to menu.lst. Please let me know if this looks right:

title Windows Vista
root (hd1,0)
chainloader +1

I guess this entry would go after the one for Windows 7? I didn't think I'd be using the savedefault and makeactive commands?

I've read through some of the links you all have provided for me. I have to admit that I am very confused using GRUB, but would like to learn how to use it.

I still want to boot into the GRUB menu and be able to select the OS to boot to.

I don't want to screw anything up this is why I proceeding in baby steps.


Any help will be appreciated.

Thanks,
Angus

---

### Post by angus1000 on 2009-05-30
I got it working with this:

[COLOR=Black][COLOR=#000000][COLOR=#0000bb]title Windows Vista Home Premium 
root [/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]hd1[/COLOR][COLOR=#007700],[/COLOR][COLOR=#0000bb]0[/COLOR][COLOR=#007700]) 
[/COLOR][COLOR=#0000bb]savedefault 
makeactive 
map [/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]hd0[/COLOR][COLOR=#007700]) ([/COLOR][COLOR=#0000bb]hd1[/COLOR][COLOR=#007700]) 
[/COLOR][COLOR=#0000bb]map [/COLOR][COLOR=#007700]([/COLOR][COLOR=#0000bb]hd1[/COLOR][COLOR=#007700]) ([/COLOR][COLOR=#0000bb]hd0[/COLOR][COLOR=#007700]) 
[/COLOR][COLOR=#0000bb]chainloader [/COLOR][COLOR=#007700]+[/COLOR][COLOR=#0000bb]1 [/COLOR][/COLOR][/COLOR]


Now I've got a triple boot system across 2 SATA HDDs, so I'm happy it all worked out :)

I just need to boot into each OS and hide the drives for the other OSes not currently in use....

Thx.
Angus

---

### Post by Jimmynemo2 on 2009-05-30
I use a gigabyte motherboard, and one thing I love- I just push f12 during boot and can pick wich drive to boot from.

Many brands of boards have a similar feature, maybe a different key press, but good way to do it for me- I can reinstall either one, and never worry about if vista messes with my boot loader or grub not liking something. You may want to see if your computer can do that.

---

### Post by angus1000 on 2009-05-30
I have an Intel mobo which only lets me select the boot order of the SATA drives. I would have to go into BIOS each time to change the boot drive. GRUB lets me select the OS via the custom configuration file, menu.lst. So far it is working out well.

When you press F12 are you going into the mobo BIOS or is it external to the BIOS? If it is external, maybe I'll pick up a Gigabyte mobo next time I upgrade.

-Angus

---

### Post by Jimmynemo2 on 2009-05-30
Yeah with my board it is external to the bios. As it boots, I push f12 and it lists all Sata and Ata drives ANSI just highlight and push enter. Love it since I then don't worry about boot loaders and I only push f12 if I wanna boot in windows for my gaming, and otherwise it just defaults to ubuntu with no input needed. 

But yeah, if your board does do that, then I totally dig grub and have nothing against it. I just end up reloading one or the other and it kept messing with the others booting. 

Have fun.

---

