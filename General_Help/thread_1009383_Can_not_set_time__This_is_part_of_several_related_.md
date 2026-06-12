---
title: "Can not set time  This is part of several related issues"
date: 2008-12-12
forum: General Help
---

### Post by Lostin60's on 2008-12-12
I had Windows and Ubuntu installed on 3 partitions (one was swap). The first thing that happened is that Ubuntu reset my clock by about 5 hrs. I was set to correct time zone during install, but otherwise, all went well.  I had to uninstall Ubuntu. When I reinstalled Ubuntu, it would not recognize my Windows install. That being the case I did not have access to my wireless internet drivers. Oh, when installing, Ubuntu "recognized ?" something because it showed my windows partition as used, but classified it  as unknown. I thought it might be just an install glitch, so  I uninstalled again. The result is..One partition program says windows is "not mounted". When I run w32tm /resync in windows I get error <0x800706ba> The RPC server is unavailable. When I run chkdsk /f I get " the file type is NTFS. Cannot lock current drive.  Chkdsk cannot run because the volume is in use by another service." I have a log error that says "The time service has not been able to synchronize the system time for 49152 seconds because the time difference is too great."  That may not be ecact, but it is close. I had also read, while researching this issue, that it also caused printer issues. So I tried to print a document, with no success. Well, no success till 3 hrs later, when it printed. The original print job, that is, not a retry. I have checked Reg. settings. I ran a Reg. repair tool. I ran McAffee. I am out of options. This is such a strange set of occurrences, that I am completely baffled. I have found no help in any windows forums.  My thoughts are that is is a combination of partitions program conflicts, and the 5 hr. time reset.  However, noob that I am, one can probably take that with a grain of salt. Any ideas would be greatly appreciated. One more thing, other than the above, Windows seems to be running fine. Go figure.

---

### Post by tomtom1982 on 2008-12-12
Only for your "unknown" windows partition:
Did you have the ntfs-3g driver installed?

If not, open a terminal and type

```
sudo apt-get install ntfs-3g
```

After this, you should have access to your Windows-partition.

---

### Post by CatKiller on 2008-12-12
You can set the time that your motherboard thinks it is (the hardware clock) in the BIOS. This is the time that's used as a reference for the time in both Windows and Ubuntu, and both of these are able to adjust this time.

It is standard in Windows to set the hardware clock to local time, and just display a Time Zone that doesn't really do anything, since the hardware clock is already set for that Time Zone.

It is standard in UNIX, and subsequently Linux, to have all hardware clocks set to Coordinated Universal Time (UTC) and only do the Time Zone translation when the time is actually displayed to the user.

It is possible to change whether Ubuntu uses UTC for the hardware clock by running the command ```
sudo nano /etc/default/rcS
``` and changing the line that says ```
UTC=yes
``` to ```
UTC=no
```

It is apparently possible to change whether Windows uses UTC for the hardware clock by changing the registry key ```
HKLM\SYSTEM\CurrentControlSet\Control\TimeZoneInformation\"RealTimeIsUniversal"
``` to 1

---

### Post by Lostin60's on 2008-12-12
> **tomtom1982 said:**
> Only for your "unknown" windows partition:
Did you have the ntfs-3g driver installed?

If not, open a terminal and type

```
sudo apt-get install ntfs-3g
```

After this, you should have access to your Windows-partition.


The "unknown" was a partition manager issue, while Ubuntu partitioned prior to install. With all the issues I have, I have not reinstalled Ubuntu yet. However, with previous installs, Ubuntu always recognized windows. Oh yes, I almost forgot, after the install of Ubuntu, Windows_XP shows up in "places".  When I access it Ubuntu says it cannot mount the volume. I am soooo confused. I do thank you for the reply, though.

---

### Post by Lostin60's on 2008-12-12
I have a new wrinkle. Since so much advice involved using the terminal, I attempted to reinstall Ubuntu. This time, Ubuntu saw the entire drive as empty, and would only let me use the entire drive as a partition. So, I ran the cd live. Not only did it show the Windows_XP in places, it also allowed me access. What the heck is going on?? I am lost.

---

### Post by Lostin60's on 2008-12-12
Yet another confusing thing I forgot to mention. When I uninstalled Ubuntu I ran "kill disk" on all of the drive, except where windows is located. Kill disk is a disk wiping utility. Kind of a phase 1 security cleaning. However when I re started windows, it attempted to use the boot manager. I had tor run "fixmbr" to get it to boot. Curiouser and curiouser.

---

