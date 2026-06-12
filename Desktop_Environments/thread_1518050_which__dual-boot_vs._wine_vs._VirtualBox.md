---
title: "which:  dual-boot vs. wine vs. VirtualBox"
date: 2010-06-26
forum: Desktop Environments
---

### Post by SaintDanBert on 2010-06-26
There are some things that I cannot accomplish without some windows applications. (No, I'm not a gamer.)  Currently, I dual boot win-XP.  I want to get rid of that if possible and consider Wine or VirtualBox.

Part of the answer is "... it depends on what you want to run ..." Yes, I know that, but I want to focus on the two platforms themselves.

Option 1 -- install Wine and try my pesky applications

Option 2 -- install VirtualBox on Ubuntu Lucid and try my pesky applications.

Which option needs more computer horsepower?
How do I know if I have enough horsepower for either one?
'lshw' reports that I have "Intel Core2 Duo at 1.6 GHz".

There is a lot to like about the V-box apporach, but it seems to take a big bite out of head space and system admin time.

Your thoughts?
~~~ 0;-Dan

---

### Post by PhilGil on 2010-06-26
I use both.

I would try Wine first and see if your apps work.  Wine is nice because applications run seamlessly and you don't have to wait for a VirtualBox Windows machine to boot. 

If you need apps that don't work in Wine then VirtualBox is the next best option.  You'll need to assign enough RAM to the virtual machine to run Windows and the applications you want to use.  RAM assigned to an open virtual machine is unavailable to Ubuntu, so the limiting factor is your system RAM rather than your CPU.

On my home system (with 2GB of RAM) I assign 512 MB to my XP virtual machine.  On my office computer (with 1GB of RAM) I assign 256 MB to my Win 2000 virtual machine.  I would expect Vista or Win 7 to need 1GB of RAM or more to run decently in VirtualBox.

---

### Post by SaintDanBert on 2010-06-26
I have 4 GB ram on my workstations along with 500 GB of total disk.
(Part of the disk is the dual boot win-XP and NTFS "data" partitions.)
That said, 1 GB for V-box will likely present no trouble.

Does my 1.6 GHz Intel Core-2 Duo provide enough horsepower for either Wine or V-box?

If I want to try Wine, can you recommend a good and thorough Getting Started with Wine guide?

~~~ 0;-Dan

---

### Post by David Batty on 2010-06-26
Which windows aps do you want to run? Because a better longterm solution would be to replace them with equivilent Linux ones. For instance I have recently switched to using Scribus from In-design.

---

### Post by d3v1150m471c on 2010-06-26
search for native software to do the job but it wouldn't hurt to try wine. However for performance go for virtual box if your system can handle it. Dual boot if absolutely necessary IMO.

---

### Post by goodolandy on 2010-08-05
There are some programs that will not install in either Wine or VirtualBox as I discovered back in late February when I decided to make Linux my primary operating system.  For me the software package was Adobe CS3.  It appears to be extremely picky on the hardware and if it does not detect certain motherboard features it will crash at the end of the install.

I have looked at Gimp as a replacement for Photoshop but that program got me so frustrated that I nearly ripped my hair out trying to get it to do something that is so easy in Photoshop.

---

### Post by Ginsu543 on 2010-08-06
@OP:
I personally run a Windows XP guest inside my Lucid host using VirtualBox because I need to run two Windows-native apps (BibleWorks and iTunes). Both programs run flawlessly in VirtualBox (as well as Microsoft Office, although I don't use it much because I use OpenOffice instead). As you can see in my siggy, I have enough system resources to devote 1 cpu core and 2 GB of ram to the VM and my Windows XP runs more smoothly and faster than when I used to run it natively on previous systems.

@goodolandy:
Have you ever tried [_GIMPshop_](http://www.gimpshop.com/)?

---

