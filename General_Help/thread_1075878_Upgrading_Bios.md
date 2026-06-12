---
title: "Upgrading Bios"
date: 2009-02-20
forum: General Help
---

### Post by Linuxidiot on 2009-02-20
Hi, Im currently working on a new task of updating my bios, the reason i want to do this is because I think it will help me overcloak my cpu, my current versoin of bios does not allow that I think, but just to check my bios version is gc11010m.15a.0009 on an E-machines.I know there are plenty of warnings about doing this, but i enjoy messing around with my computer and i want to increase its performance because its not all that great atm.
 I downloaded a exe file from emachines thats supposed to update the bios, but under the description it says its for windows.The reason I made this thread is to ask that if i did in fact update the bios would it hurt my current file system, or possibly corrupt anything.Also any suggestions would me appreciated.

---

### Post by Rhubarb on 2009-02-20
I don't have any experience with emachines, and I don't know if it's possible to extract the binary BIOS image from the exe file.

But, have a good look at this thread:-
[http://ubuntuforums.org/showthread.php?t=318789](http://ubuntuforums.org/showthread.php?t=318789)

The thread helped me out a lot.

---

### Post by punx45 on 2009-02-20
[http://ubuntuforums.org/showpost.php?p=6690466&postcount=3](http://ubuntuforums.org/showpost.php?p=6690466&postcount=3)

---

### Post by bodhi.zazen on 2009-02-20
Just take great care to use the correct BIOS, updating the BIOS can cause problems and there is no "undo button".

---

### Post by punx45 on 2009-02-20
yeah, if you  choose the wrong version, or interrupt it during install, byebye mobo.  if you have a floppy drive, i suggest backing up the current bios if your board supports that.

---

### Post by Skripka on 2009-02-20
> **bodhi.zazen said:**
> Just take great care to use the correct BIOS, updating the BIOS can cause problems and there is no "undo button".

Indeed.  Flashing a BIOS is risky.  Trying to Flash a BIOS from an EXE on a *buntu only system is playing with fire.

@OP:  Do you for certain know that a newer BIOS would even do anything for multiplier/voltage/FSB tweaking?  Even it it does-are you certain your PSU can handle higher outputs?  Cheap machines usually come with cheap PSUs (low power, and %), hence the question.

---

### Post by Linuxidiot on 2009-02-20
Well, this machine wasnt bad in its day...but that was a few days ago :)
 I am currently researching the newer bios to answer those questions, and the processor is upgradeable, but i like to learn by "trial by fire" method :)

---

### Post by Linuxidiot on 2009-02-20
I have confirmed that this is the correct upgrade, the instructions are for windows though, so im wondering if i should convert this into a iso file and use it like a startup disk or maybe a mount method. I will check out some other threads to get some more opinions about how to follow up on this. please feel free to make some more suggestions:)
 I know i might get some flamage about this but Im also curious if wine could handle this task or if i should even consider this

---

### Post by punx45 on 2009-02-21
most bios exes run in dos, and the links provided earlier show you how to build a bootable cd to accomplish that.

---

### Post by Slim Odds on 2009-02-21
So you're going to go through all this trouble for maybe a 10% gain.

With the powerful dual core or quad core these days, overclocking is just way more trouble than it's worth.

---

