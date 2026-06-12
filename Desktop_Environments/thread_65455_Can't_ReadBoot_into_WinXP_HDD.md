---
title: "Can't Read/Boot into WinXP HDD"
date: 2005-09-14
forum: Desktop Environments
---

### Post by koggo on 2005-09-14
I just installed Kubuntu onto my AMD and I have Kubuntu on one 40gb HDD & WinXP on another 120gb HDD.

When I boot the PC it loads straight into Kubuntu, without an option for the other WinXP drive. I know that this is configurable somewhere in GRUB though, right?

When I go to media:/hdb1 in Konqueror (the WinXP drive), it says:

Could not mount device.

The reported error was:

mount: can't find /dev/hdb1 in /etc/fstab or /etc/mtab


...and when i go to /dev/hdb1 it says:

You do not have enough permissions to read file:///dev/hdb1


Does anyone know how to fix this?
Sorry if I sound stupid, but im a complete n00b to this.

Thanks.

---

### Post by cwaldbieser on 2005-09-14
[QUOTE=koggo]I just installed Kubuntu onto my AMD and I have Kubuntu on one 40gb HDD & WinXP on another 120gb HDD.

When I boot the PC it loads straight into Kubuntu, without an option for the other WinXP drive. I know that this is configurable somewhere in GRUB though, right?

When I go to media:/hdb1 in Konqueror (the WinXP drive), it says:

Could not mount device.

The reported error was:

mount: can't find /dev/hdb1 in /etc/fstab or /etc/mtab


...and when i go to /dev/hdb1 it says:

You do not have enough permissions to read file:///dev/hdb1


Does anyone know how to fix this?
Sorry if I sound stupid, but im a complete n00b to this.

Thanks.[/QUOTE]
This link should tell you what you need to do:
[http://www.ubuntuguide.org/#windows](http://www.ubuntuguide.org/#windows) 

I think you basically just need to add an entry to the /etc/fstab config file.

---

### Post by koggo on 2005-09-14
OK, using those directions I can mount the HDD but I still can't boot into Win.

As in what do I put for the

title  
root  
kernel  
initrd
savedefault
boot

... Stuff?

---

### Post by koggo on 2005-09-14
Bit of a problem now, I used this code:

title		Microsoft Windows
root		(hd0,1)
savedefault
makeactive
chainloader	+1

And now when I boot i get the error: NTLDR Is Missing
I did a google & found this *is*  to do with booting, so what now?
Do I physically remove the Kubuntu HDD?
Or What?

---

### Post by f1dave on 2005-09-14
From what I remember, that means it cannot find the windows nt boot loader to load  your windows version. Are you sure your windows partition is (0,1)? 

I have 2 partitions on the one drive, (0,0) is kubuntu and (0,1) is windows. But your setup will be different, so you might have windows on (2,0) or something. Have a read up on how GRUB and LILO work with reference to the addresses of drives and work it out from there.

---

### Post by koggo on 2005-09-14
[QUOTE=f1dave]From what I remember, that means it cannot find the windows nt boot loader to load  your windows version. Are you sure your windows partition is (0,1)? 

I have 2 partitions on the one drive, (0,0) is kubuntu and (0,1) is windows. But your setup will be different, so you might have windows on (2,0) or something. Have a read up on how GRUB and LILO work with reference to the addresses of drives and work it out from there.[/QUOTE]
 I wasn't exactly sure which one was the windows one but I was going through trying to get it.
Then when i used (0,1) it Showed the 

title Microsoft Windows
root (hd0,1)
savedefault
makeactive
chainloader +1

Stuff and just stopped. So I restarted & It had the other error. Any way to fix it?

---

### Post by roblubbers on 2005-09-15
because grub uses another numbering system you need to know what it is under Kubuntu so you can use this table:

translation for kubuntu --> grub
hda1     hd(0,0)
hda2     hd(0,1)
hda3     hd(0,2)

hdb1     hd(1,0)   ---> you should probably use this one!!!
hdb2     hd(1,1)
hdb3     hd(1,2)

---

### Post by koggo on 2005-09-15
[QUOTE=roblubbers]because grub uses another numbering system you need to know what it is under Kubuntu so you can use this table:

translation for kubuntu --> grub
hda1     hd(0,0)
hda2     hd(0,1)
hda3     hd(0,2)

hdb1     hd(1,0)   ---> you should probably use this one!!!
hdb2     hd(1,1)
hdb3     hd(1,2)[/QUOTE]
 OK, but is there **any way to edit grub?!?!**

---

### Post by f1dave on 2005-09-15
Sure is.

edit the file /boot/grub/menu.lst

---

### Post by koggo on 2005-09-16
[QUOTE=f1dave]Sure is.

edit the file /boot/grub/menu.lst[/QUOTE]

But I can't boot Kubuntu!!

---

### Post by f1dave on 2005-09-16
Then while in grub, press e on the entry you wish to edit, then e on the line of the entry to edit.

Then b to boot the entry. Then edit the file inside kubuntu once booted.

---

### Post by koggo on 2005-09-16
[QUOTE=f1dave]Then while in grub, press e on the entry you wish to edit, then e on the line of the entry to edit.

Then b to boot the entry. Then edit the file inside kubuntu once booted.[/QUOTE]
 Can't get to GRUB either. The error shows before GRUB loads.

---

### Post by f1dave on 2005-09-16
Ok... so lets clarify here.

You turn your computer on, it goes through the bios, scans for bootable cds or whatever and then gives you the NTDLR error?

---

### Post by koggo on 2005-09-16
Yes.

---

### Post by f1dave on 2005-09-16
From your posts, I take it that kubuntu and windows are on two different drives, and that the kubuntu drive is the booting one. I therefore find it odd you're seeing an NTDLR error without seeing GRUB, since I thought that was associated with windows...

---

### Post by koggo on 2005-09-16
Yes theyre on two different drives.
I'm pretty sure that the Kubuntu one is the booting one.
But i have no idea why it's happening.

---

### Post by koggo on 2005-09-16
OK, im back into Kubuntu.
I physically deattached the Windows Drive & booted into Kubuntu & edited my GRUB list.

Now I just need to get GRUB working to boot into Windows.
I tried it with 1,0 but it didnt work.

Now what?

---

### Post by f1dave on 2005-09-16
Ok, glad to hear you've made some progress.

First up, list the drives you've got under kubuntu... hda1, hdb1, etc... This will help us in working out what we should list your windows drive as in grub. It's very important that you get correct just which drives are which, ie hda1 is linux, hdb1 is windows, etc.

---

### Post by koggo on 2005-09-17
hda  - Main Kubuntu Partition
hda2 - Something to do with linux I assume
hda5  - see hda2 but it's a 1.5gb partition.
hdb1 - Windows.

I created a boot disk for Windows & booted into it that way, and I read the Microsoft Knowlege Base article, got the bcupdate2.exe utility and now it's totally stuffed up, M$ are bastards. I can't even boot from a floppy anymore. HEEEEEEEEEELLLLLLLLLLLPPPPPPPPPPP!!!!!!!!!!!

---

