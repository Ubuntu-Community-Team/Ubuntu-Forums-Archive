---
title: "Daft suicidal son and uninstal"
date: 2009-05-11
forum: General Help
---

### Post by paulcliman on 2009-05-11
my son has tried to uninstal Ubuntu by following an online video<
He deleted the Linux directories and was then asked to insert a Windows Vista disk which he hasn't got - Acer computer with recovery disk which didn't work
Now he has "GRUB loading, please wait.
Error 22" with computer all but dead 
Is there any way of re;oving or recovering Windows Vista from such a position?
Thanks in anticipation

---

### Post by scottuss on 2009-05-11
If he has deleted the Windows partitions that were on the computer, then no. You no longer have Windows on your computer.

If you have an Acer recovery disk, you can restart the computer, set the BIOS to boot from CD (you may need to hit F2 to enter setup or something like that)

When the computer boots from the CD, run through the Acer installation to put Windows back on there.

It sounds like he has messed it up to be honest. If the Acer CD doesn't work, you will need to get a Vista disc or re-install Ubuntu.

---

### Post by skymera on 2009-05-11
> **paulcliman said:**
> my son has tried to uninstal Ubuntu by following an online video<
He deleted the Linux directories and was then asked to insert a Windows Vista disk which he hasn't got - Acer computer with recovery disk which didn't work
Now he has "GRUB loading, please wait.
Error 22" with computer all but dead 
Is there any way of re;oving or recovering Windows Vista from such a position?
Thanks in anticipation

Hmm could be a sticky pickle.
Deleting the Linux directories will definately break Ubuntu but leave Windows intact.

UNLESS. Was Windows mounted???
If it was mounted for example on /media/windows
and /media was deleted. Your Windows has also been wiped.

Reinstall Windows using the recovery or install disk.

Just out of curiosity, which video was it?
Seems obsurd that deleting the directories is called "uninstalling".

---

### Post by paulcliman on 2009-05-11
He deleted just the Ubuntu partitions leaving C and D - he swears
We made a Vista Recovery Disk ISO from downloading from my computer but it stopped booting looking for A:ibmdos.sys ???
So ...... if the Vista and Data partitions are still there is there any hope of retrieval ?
If not, can he buy a copy of Windows Vista and somehow remove GRUB and start from scratch ?
Where is GRUB and can it be deleted ?
Thanks again for your szift response

---

### Post by skymera on 2009-05-11
Did he delete the Ubuntu partitions from Windows or from Ubuntu itself?

If he did it from Windows, that explains why you cannot boot.
GRUB no longer exists on the hard drive.

If that's the case, you just need to fix the MBR.
SuperGRUB Disk can be used to recover Windows MBR.

---

### Post by paulcliman on 2009-05-11
> **skymera said:**
> Hmm could be a sticky pickle.
Deleting the Linux directories will definately break Ubuntu but leave Windows intact.

UNLESS. Was Windows mounted???
If it was mounted for example on /media/windows
and /media was deleted. Your Windows has also been wiped.

Reinstall Windows using the recovery or install disk.

Just out of curiosity, which video was it?
Seems obsurd that deleting the directories is called "uninstalling".

we did a search of Google for uninstalling Ubuntu and found this video uninstall "tutorial" fairly easily - just one or two items down.

---

### Post by HavocXphere on 2009-05-11
Boot into win recover console and use fixmbr (or was it mbrfix...). It the windows files are still there then this should replace grub with the windows bootloader. Once windows is working again then you can fix ubuntu...its easier that way around.

Oh and put a BIOS password on the box.

---

### Post by paulcliman on 2009-05-11
If I can get a MSDOS bootable CD made, could I do it from there ?
He has NO floppy drive on his computer

I downloaded two different versions of SuperGRUB onto bootable CDs and BOTH gave the message =
1, FD 1.44 MB System Type - 06
Starting Caldera DR=DOS
Can't load BDOS kernel file: A:\IBMDOS.COM
System halted

---

### Post by northern lights on 2009-05-11
You've downloaded the Floppy version. Download the [CD .iso]("http://www.supergrubdisk.org/index.php?pid=5").

---

### Post by paulcliman on 2009-05-11
> **northern lights said:**
> You've downloaded the Floppy version. Download the [CD .iso]("http://www.supergrubdisk.org/index.php?pid=5").

First I must thank you all for such patience, support and speed in responding - much appreciated.
I did as you said and got EXACTLY the same message ! Weird !
I have also tried to reinstal Ubuntu - got to 53% and it hung.
The only CD I have which actually boots is GPartEd.
This reports
/dev/sda1  PQSERVICE don't know what this is
/dev/sda2   ACER  thats his C drive
/dev/sda3   DATA   thats his D drive
/dev/sda4  Extended where Linuxd was, I suppose

If I delete PQSERVICE (whatever it is) and ACER (where windows is) could I then install an earlier version of Windows in this space? 
We have a full Acronis True Image backup of his C drive and could therefore probably restore it to its Vista glory?
What do you think ?

---

### Post by paulcliman on 2009-05-12
Lqtest nezs //
I have now succeeded in downloading the Universal Boot CD, which does actually boot !
Howeverm I can't find any application on it which ;ight solve ;y son's problem.
Any further help please ??

---

