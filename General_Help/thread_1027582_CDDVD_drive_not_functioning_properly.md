---
title: "CD/DVD drive not functioning properly"
date: 2009-01-01
forum: General Help
---

### Post by Aralhach on 2009-01-01
I installed a brand new Ubuntu system yesterday from scratch (nothing else on the computer).  Everything else is working fine.

The problem is that when I put a disk in (say a movie), when I finish using it and want to eject it, it goes back in as soon as it's done going out.  Like, it goes out and then goes in instantly.  This happens when I eject from the File Manager and also happens when I hit the Eject button on the drive.  It stays open when I want to put a disk IN though (when the tray is empty).

Could anyone help me with this?? (it's a pretty big nuisance)

Thanks in advance!

---

### Post by oilchangeguy on 2009-01-01
> **Aralhach said:**
> I installed a brand new Ubuntu system yesterday from scratch (nothing else on the computer).  Everything else is working fine.

The problem is that when I put a disk in (say a movie), when I finish using it and want to eject it, it goes back in as soon as it's done going out.  Like, it goes out and then goes in instantly.  This happens when I eject from the File Manager and also happens when I hit the Eject button on the drive.  It stays open when I want to put a disk IN though (when the tray is empty).

Could anyone help me with this?? (it's a pretty big nuisance)

Thanks in advance!

copy and paste these lines into the terminal:
Originally Posted by fr34k  
Copy-Paste and execute the following two commands. It instantly fixed my problem , without any Internet updates or Reboots. The first command is just to backup the rules files before editing.


Code:
sudo cp /etc/udev/rules.d/60-persistent-storage.rules /etc/udev/rules.d/60-persistent-storage.rules_bkpCode:
sudo sed -i 's/ENV{DEVTYPE}=="disk", KERNEL!=/ENV{DEVTYPE}=="disk", KERNEL==/g' /etc/udev/rules.d/60-persistent-storage.rulesFrom : [http://mobilevs.blogspot.com/2008/11...-rom-tray.html](http://mobilevs.blogspot.com/2008/11...-rom-tray.html) 

Fr34k:

Applying ALL of the Intrepid updates (including proposed updates) did not fix my CD ejection/closing problem BUT your 2 lines of terminal command codes DID fix it.

You would think that if you know about this ERROR in coding, that the developers of Ubuntu would know about this and correct this coding error.

If I have misinterpreted what is going on here, someone please correct me.

But in any case the above commands finally fixed my problem.

Thanks.

---

### Post by Aralhach on 2009-01-01
Thanks a lot for your response!!  I ran the update (I just installed it) and the update has fixed my problem.

I will save your couple lines of code though, as it might prove useful in the future.

Again, thanks for your time!!

---

