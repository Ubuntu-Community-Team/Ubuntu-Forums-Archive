---
title: "Searching for help?"
date: 2009-04-12
forum: General Help
---

### Post by SylviaCh on 2009-04-12
Hi, I run the vista home premium and after being prompted to run a windows update, 0x80070002, the computer would not start.  I would get to the blue start-up pade then a startup repair would kick in, then a message from Microsoft Windows telling me startup can not repair.
I did all the usual, system restores to all dates (nada), ran all the tests on the computer, tried to go to safe mode, did not work, tried last known config, ditto...
All I need are two word docs - can I get them or are they lost?

Someone suggested Unbuntu so I downloaded, tried F12 to reboot with the CD but again... same window to MS...
Any help?
Thanks so much
Sylvia

---

### Post by paradigm2 on 2009-04-12
> **SylviaCh said:**
> Hi, I run the vista home premium and after being prompted to run a windows update, 0x80070002, the computer would not start.  I would get to the blue start-up pade then a startup repair would kick in, then a message from Microsoft Windows telling me startup can not repair.
I did all the usual, system restores to all dates (nada), ran all the tests on the computer, tried to go to safe mode, did not work, tried last known config, ditto...
All I need are two word docs - can I get them or are they lost?

Someone suggested Unbuntu so I downloaded, tried F12 to reboot with the CD but again... same window to MS...
Any help?
Thanks so much
Sylvia

Well often the BIOS is set so that it will first try to boot from the hard drive.  So if it sees a boot record on the hard drive it will try to boot from it there and never try to boot from the CD.  You might want to check this within your BIOS.

To do that usually there is a key you can press at startup to get into the bios.  Sometimes it is F2, F10, F12, or DEL.  Once you get in look for an entry which says something like "boot options" or "boot order".

Edit:

I don't know if the ubuntu live CD will be able to read your existing windows partition as it is or not.  My gut feeling is "no".  You should probably just use a windows rescue disk to copy that file over to a floppy or something.  Maybe repair the windows install.  I know there are special utilities which are meant to help with this, however you need a way to get the files off the computer.  If those files are important try to get them ASAP and without modifying the computer much until you do get them as there is a risk that what youtry might make it harder or impossible to get.  More so than it already is.

---

### Post by SylviaCh on 2009-04-12
thanks para, will try

---

### Post by iponeverything on 2009-04-12
I think that there is good chance that the live CD will will be able to read the windows disk.

I do think that you might need to check your bios to set the CD has the primary device as paradigm2 suggested.

---

