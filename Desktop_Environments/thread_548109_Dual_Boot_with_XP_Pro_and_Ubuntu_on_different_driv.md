---
title: "Dual Boot with XP Pro and Ubuntu on different drives"
date: 2007-09-10
forum: Desktop Environments
---

### Post by you_silly_motals on 2007-09-10
Hey everybody, I am brand new to linux, but I want to give it a shot. I installed ubutu 7.04 just fine but after restarting I can't boot into ubuntu. There is no dialog for choosing the operating system at all, it just doesn't see it.  >: <

Anyway this is how I am set up:

SATA Hard drive 1: 80 (Linux)
SATA Hard drive 2: 320 (data)
SATA Hard drive 3: 320 (XP Pro)
SATA Hard drive 4: 160 (data)
IDE Hard drive 5: 320 (data)

The numbers mean nothing, BTW.

From what I understand most of the reason I can't get ubuntu to boot is because something called "grub" didn't replace the windows BOOT.INI since I installed ubuntu on a different drive than windows.

So I ask you, how do I get dual boot working?

---

### Post by merlinus on 2007-09-10
You might try supergrub.

Download:

[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

Info on its use here:

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by you_silly_motals on 2007-09-11
I got that CD and tried using it. It doesn't seem to have worked. Although I really don't know what I'm doing at all.

---

### Post by merlinus on 2007-09-11
Did you read the extensive, step-by-step directions at the second link?

---

### Post by Jouke74 on 2007-09-11
No supergrub required....

Change the boot order of your hardisks in the BIOS will probably help :)

SATA Hard drive **1**: 80 (Linux)
SATA Hard drive 2: 320 (data)
SATA Hard drive **3**: 320 (XP Pro)  
SATA Hard drive 4: 160 (data)
IDE Hard drive 5: 320 (data)

Windows boot is on the SATA disk 3 MBR (Master boot record).
Grub boot is on the SATA disk 1 MBR. 

In your BIOS the boot order will probably be 3 1, hence the boot sequence will never see grub, as it sees only the windows MBR and thus will start windows.
Change this to 1 3 and then Grub will be read first, giving you the option to choose between windows (which then links to MBR from disk 3) or ubuntu which links to the Kernel init.

---

### Post by you_silly_motals on 2007-09-11
Alright I did that and this came up:
[[IMG]http://img411.imageshack.us/img411/461/p9111761hk1.jpg[/IMG]](http://img411.imageshack.us/my.php?image=p9111761hk1.jpg)
I assume that this is GRUB.

Anyway even though I get this, I can't load neither ubuntu nor windows.
When I try to load linux I get a screen saying: 
Error 17: Cannot mount selected partitiion

When I try loading XP Pro I get a screen saying:
Starting up ...
_

But then nothing happens.

When I installed Ubuntu I noticed an option to install the boot loader to a different drive. But the way you identified the drive to install to is foreign to me and I have no idea which drive to designate. If I'm reading it right I could install ubuntu on the one drive and GRUB on the windows drive correct?

EDIT: I used this option last time I installed Ubuntu, I may or may not have selected the correct drive because I have two identical 320 gb drives, and one of them is the one I want GRUB on.

---

### Post by logos34 on 2007-09-11
> **you_silly_motals said:**
> I could install ubuntu on the one drive and GRUB on the windows drive correct?

Yes.

Try editing the kernel entry on the grub menu:

Hit 'e' key on the kernel at the top.  Hit 'e' again on the 'root' line.  Change to **(hd0,0)** if root is the first partition on the ubuntu disk, or (hd0,1) if second, and so on.  After change hit enter and 'b' to boot. If that gets you into linux then you can make the change permanent in /boot/grub/menu.lst

---

### Post by you_silly_motals on 2007-09-11
Alright, that worked thanks logos34! (for linux anyway) 

Is it safe to assume that the same thing would work for XP Pro?

---

### Post by Jouke74 on 2007-09-11
I used your nice schematic to figure out that part :) 

SATA Hard drive 1: 80 (Linux) < so here's Ubuntu installed and Ubuntu uses the MBR for this disk standard to place GRUB.

SATA Hard drive 3: 320 (XP Pro) < Here is XP, so here the MBR of XP resides. 

Good luck with the rest, I only have two harddisks and my grub is basically on my data drive. This is handy, in case you want to reinstall windows, you just switch around the boot-sequence in BIOS again and you don't need use Supergrub or Windows recovery disks to get the MBR's working in the right way. 

Good luck.

---

### Post by logos34 on 2007-09-11
> **you_silly_motals said:**
> Alright, that worked thanks logos34! (for linux anyway) 

Is it safe to assume that the same thing would work for XP Pro?

no, for windows your have to do a few tricks with the drive mapping to perform what's called a 'virtual swap:

[http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html#DOS_002fWindows](http://www.gnu.org/software/grub/manual/html_node/DOS_002fWindows.html#DOS_002fWindows)
[https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs](https://help.ubuntu.com/community/How_to_dual-boot_Ubuntu_and_XP_after_installing_them_separately_on_two_HDs)
[http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk](http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk)
[http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands](http://users.bigpond.net.au/hermanzone/p15.htm#Chainloading_Windows_using_map_commands)
[http://ubuntuforums.org/showthread.php?t=179902](http://ubuntuforums.org/showthread.php?t=179902)


So, assuming the drive order listed above (XP 3rd), your menu.lst entry for windows should look something like this:

> # This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdc1
title		Windows XP
root		**(hd2,0)** --->or try 'rootnoverify'
[B]map            (hd0) (hd2)  
map            (hd2) (hd0)[/B]
savedefault
makeactive
chainloader	+1

Make sure /boot/grub/device.map corresponds to the BIOS disk order.  So for ubuntu first and windows third it should show '**(hd0) /dev/sda**' and '**(hd2) /dev/sdc**'

Hope it allows you to boot XP from grub.  In my experience it's sometimes hard to get it to work unless you move windows to second position (hd1).

---

