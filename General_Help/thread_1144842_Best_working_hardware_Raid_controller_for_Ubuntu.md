---
title: "Best working hardware Raid controller for Ubuntu ?"
date: 2009-05-01
forum: General Help
---

### Post by astronaute on 2009-05-01
Hello,

(I think I initially posted this in wrong section, sorry for that)

**Problem**:
**_[COLOR=Blue]I need a dual boot system with Windows XP64 and Ubuntu on RAID 0.[/COLOR]_**
_**[COLOR=Blue]I will also need another RAID 1 array for storage, so a total of 4 hard disks.[/COLOR]**_

Actually I have ICH9R FakeRaid controller on my motherboard (Asus P5E3), but Ubuntu Jaunty refuses to recognize it (alternate CD): 

[http://ubuntuforums.org/showthread.php?t=1136737](http://ubuntuforums.org/showthread.php?t=1136737)

Some people suggest buying real **hardware controller**, so I goggled few hours and found this card Adaptec 1430SA :
[http://www.ldlc.com/fiche/PB00069832.html](http://www.ldlc.com/fiche/PB00069832.html)
(**PCIe x4, 4 ports, perfect**)

...and also I found problems associated with it :

[http://www.uluga.ubuntuforums.org/showthread.php?p=4262861](http://www.uluga.ubuntuforums.org/showthread.php?p=4262861)
[http://ubuntuforums.org/showthread.php?t=521394](http://ubuntuforums.org/showthread.php?t=521394)
[http://ubuntuforums.org/showthread.php?t=877285](http://ubuntuforums.org/showthread.php?t=877285)

So now, few days later, I'm tired of trying to install Ubuntu which I suspect not being mature enough for anything other then basic Raidless systems :)

If anyone here can help me choose the perfect **hardware controller fully supported by Ubuntu** in order to solve my problems, or even help me install windows and ubuntu on my current FakeRaid, it would be wonderfull :)

I would like to install Ubuntu as I am familiar with debian for servers, but if you tell me that **another linux distribution** can work better on my setup, I will try it.

Thank you in advance !!!!

---

### Post by astronaute on 2009-05-01
[FONT=Arial][SIZE=2]I found this one too (a bit expensive) ;

3Ware 9650SE-4LPML
[http://www.3ware.com/products/serial_ata2-9650.asp](http://www.3ware.com/products/serial_ata2-9650.asp)

On their site, they say that Linux is supported, what that means exactly?
Do I have to include drivers for it on the Live CD somehow?

I don't understand why we need drivers for it, it is not supposed to "just work" without knowing that it is a Raid array? 

I am confused :)
[/SIZE][/FONT]

---

### Post by cbraxton on 2009-05-01
3Ware controllers are supported directly in the Linux kernel, there is no need for additional drivers. 3Ware also provides software configuration and monitoring tools for Linux, as well as tech support. However their products tend to be expensive once you get beyond a basic 2-port job.

---

### Post by astronaute on 2009-05-01
> **cbraxton said:**
> 3Ware controllers are supported directly in the Linux kernel, there is no need for additional drivers. 3Ware also provides software configuration and monitoring tools for Linux, as well as tech support. However their products tend to be expensive once you get beyond a basic 2-port job.

I need 4 ports minimum (Raid 0 + Raid 1), can you please recommend some other cards for ubuntu ?

---

### Post by cbraxton on 2009-05-01
> **astronaute said:**
> I need 4 ports minimum (Raid 0 + Raid 1), can you please recommend some other cards for ubuntu ?

Maybe someone else would have a recommendation -- 3Ware RAID controllers are the only ones I've used on Linux systems, as they usually "just work" out of the box without a lot of fiddling needed. (Of course I'm typically installing them in servers where the cost is not as much of an issue.)

---

### Post by dawnlove on 2009-05-01
open suse has no problems with false raid.

---

### Post by fjgaude on 2009-05-01
FakeRAID BIOS style seems to work for most folks after understanding and installing **dmraid**.

---

### Post by astronaute on 2009-05-06
> **fjgaude said:**
> FakeRAID BIOS style seems to work for most folks after understanding and installing **dmraid**.

You apparently did not read the other thread where I post screenshots of alternate cd install with dmraid, right? :)

[http://ubuntuforums.org/showthread.php?t=1136737](http://ubuntuforums.org/showthread.php?t=1136737)

---

