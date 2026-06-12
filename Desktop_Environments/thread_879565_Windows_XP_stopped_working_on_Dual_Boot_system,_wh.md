---
title: "Windows XP stopped working on Dual Boot system, while Ubuntu works fine (&lt;3 Ubunu)"
date: 2008-08-04
forum: Desktop Environments
---

### Post by AoXoA on 2008-08-04
Ok for various reasons, I have this problem. Firstly Ive a dual boot of Ubuntuo and Windows Xp on Drive C:, and on Drive E: is my storage Hard drive.

For reasons unknown, (Well ok was one of those mini heaters I think) my computer shut down, and here were the problems;

1. Drive C: Which has Ubuntu and Windows XP dual boot/installed. Well Windows XP itself will not load up, and I have no knowledge of how to find out what the BSOD (Blue Screen of Death) is saying. I used to know, but been so long since I had one.

2. While Number 1. was happening, Drive E: was stating an NTSF (The windows XP file format, NTSF is what I think its called, but maybe NTFS? Anyway) Drive E: was not able to be loaded as it was flagged "IN USE". I tried the commands from searching google of the problem, and it was not working, however a check on the WINDOWS XP CD 'repair' worked. So E: is fine, and I can access it in UBUNTU.

3. When I was doing CHKDSK, Only drive E: was showing, it had no option for C:, despite that UBUNTU works perfectly and is Partitioned/Installed on C:.

Anyway fortuantly I am quite certain I can back up most things, but preferably I would rather try to get the C: Windows XP install working instead. 

When I reboot/reset, and when Grub gives me the options of Ubuntu, and Windows XP, Ubuntu works perfectly, while Windows XP does not. They are both partitioned on the same Harddrive, (Ubuntu notices both, since its superior of course hah, and windows just noticed itself when it was working). Ubuntu can also notice the Windows XP installation still, dispite the BSOD happening when I try to Load WinXp.

Anyway, I totally forgot how to get the BSOD to a logfile, and where it will be located if I wanted to read it. I know that will help way more than other peoples experiences if they had this same problem because of hardware/software and etc, although I am definantly open to suggestions.

The main faults were with this situation, is power suddenly turning off, while playing World of Warcraft in WIN XP.

EDIT: Drive D and E are the same, My other comp uses the 2ndary as E, so unfortuantly I relate to that too much.

---

### Post by Malac on 2008-08-04
Sounds like you have 'blown' your Windows boot sector or damaged the files Windows needs to boot.
The only ways I know of fixing this are:

To fix boot sector
1. Put in the Windows CD and choose 'Recovery Console'
  Then run fixboot and fixmbr
  This will get rid of GRUB loader so you would need to re-install GRUB from the LiveCD to get your Ubuntu install to be available again. (Lots of threads on this on the forum.)

To fix damaged files.
2. Put in the Windows CD and choose Install option
    Then when it gets to a prompt something like 'Repair an Existing Windows Installation' choose the one on C:
    I can't remember if this second option will do the same to your GRUB install as well but I suspect so.

Hope this helps.

---

### Post by AoXoA on 2008-08-04
Argh that does suck lol :( Oh well guess that at least most of the info is there, my C: is only a 40GB drive, while D: is 160 (Has most the info).

This comp is kind of out-dated but its until now been really reliable :( Its amazing just how bad something like this can do. I mean I had this comp running almost 24/7 for almost a year now, and one power failure caused this :( But anyway ill try the things you suggested, and fortuantly I can back up most things at least before I go ahead =)

Quite glad I even installed Ubuntu on this machine, for some of the data/info is things I really need in the future.

---

