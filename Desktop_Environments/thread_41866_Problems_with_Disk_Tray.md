---
title: "Problems with Disk Tray"
date: 2005-06-15
forum: Desktop Environments
---

### Post by Havoc on 2005-06-15
Hello,
I have this problem with my Disk tray.It won't open with analogue means(Meaning, pressing the button on the CD Drive)!!
Most times It opens if i write "eject", but sometimes, even with sudo, it won't!
What the hell? I can delete the whole filesystem, but I can't eject a CD?
When It doesn't, with sudo, it says "CD busy, wait for an eternity".This is really annoying.It used to work, both analogue and digital eject, but now I'm stuck!
I had asked this weeks ago in the Mailing Lists and somebody said "It's a feature".Well, considering the modular nature of Linux (And Ubuntu in paticular), I DON'T LIKE THIS FEATURE, and it should be possible to disable it.There should be NO problem by doing that.  ](*,) 

Anyways, thanks.Again, thanks.And again, than.....

---

### Post by mike998 on 2005-06-15
Try unmounting the CD Drive - Linux/Unix doesn't like the forcible removal (read - ejecting) of filesystems - this is a good thing to prevent file system corruption.

---

### Post by Alexander Kirillov on 2005-06-15
[QUOTE=Havoc]Hello,
I have this problem with my Disk tray.It won't open with analogue means(Meaning, pressing the button on the CD Drive)!!
Most times It opens if i write "eject", but sometimes, even with sudo, it won't!
What the hell? I can delete the whole filesystem, but I can't eject a CD?
When It doesn't, with sudo, it says "CD busy, wait for an eternity".This is really annoying.It used to work, both analogue and digital eject, but now I'm stuck!
I had asked this weeks ago in the Mailing Lists and somebody said "It's a feature".Well, considering the modular nature of Linux (And Ubuntu in paticular), I DON'T LIKE THIS FEATURE, and it should be possible to disable it.There should be NO problem by doing that.  ](*,) 

Anyways, thanks.Again, thanks.And again, than.....[/QUOTE]
 If it says "device busy", it means that some programs are accessing the files on CD. In this case, ejecting the CD is disabled for obvious reasons. There is no easy way to override this behavior. 


Try closing all programs that may be accessing files on the disk  before ejecting it.  In Warty, there were problems with this as sometimes "busy" was due to so-called "file alteration monitor" (which is not run by user but by the system, and therefore couldn't be easily stopped) but in Hoary, this shouldn't happen.

---

