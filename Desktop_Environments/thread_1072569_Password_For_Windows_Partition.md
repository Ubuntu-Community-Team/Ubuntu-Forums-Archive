---
title: "Password For Windows Partition"
date: 2009-02-17
forum: Desktop Environments
---

### Post by SilvaRizla on 2009-02-17
I've installed Jaunty (fresh install) and I notice I now have to give a password to access my windows partition.  I didn't have to do this previously, it causes problems as my music is on my windows drive and Amarok can't request the password, it will just refuse access and not play.  To get around this I have to browse the drive in Dolphin and wait for the password prompt.

Anyone know how to get around this annoyance?

---

### Post by InspiredIndividual on 2009-02-17
It seems the Windows Partition doesn't automount anymore. I'm no expert, but this thread may be helpful in solving your problem: [http://ubuntuforums.org/showthread.php?t=828873](http://ubuntuforums.org/showthread.php?t=828873)

---

### Post by SilvaRizla on 2009-02-18
I downloaded the NTFS Config tool mentioned and added the drives for automount.  Thanks for that

---

### Post by Ravernomina on 2009-02-18
Get you windows CD and open command propt (recovery concle).

Try typing in these commands.

**_FixMbr_**-This will rewright ur master boot record. This can fix alot of boot problems in windows XP Then after u do this do the next command at the bottem.

**_Fixboot_**-This will layout ware windows is located and also ware all other patition boot to.

[SIZE="7"]AFTER THIS PLEASE MAKESURE YOU REINSTALL GRUB OR U WILL NOT BE ABLE TO BOOT INTO UBUNTU!!!!![/SIZE]

[SIZE="2"]good luck m8 :s. use this method as a 2nd to last resort.[/SIZE]the last resoft is reinstall your OSes again.

Also go into your BIOS i setting might have ben changed check to see if a password has ben set.

GL m8 :3

      Ravernomina

---

