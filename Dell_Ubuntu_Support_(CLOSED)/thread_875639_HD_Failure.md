---
title: "HD Failure"
date: 2008-07-31
forum: Dell Ubuntu Support (CLOSED)
---

### Post by yeomanrand on 2008-07-31
I decided to dual boot Ubuntu and Vista on my XPS M1530, and, long story short, just after I get everything working well and Linux begins to become an enjoyable experience, my hard drive bites the dust.

I run the Dell diagnostic program, my hard drive fails the DST and comes up with error code 2000-0146. Ubuntu still works, and Vista works only in safe mode. I haven't run chkdsk yet, but I'm pretty sure I'm SOL and am going to end up calling Dell for a replacement.

My question is, should I uninstall Ubuntu, or just leave it?

And, uh, while I'm talking to support, should I even bother to tell them that I have Ubuntu installed too?

---

### Post by rahmath on 2008-07-31
I dont think, ubuntu caused the damage on the hdd.

---

### Post by nfox on 2008-08-04
My friend's Dell failed the same way. Ubuntu's livecd works after copious errors being thrown about the hard drive. So that's running off of ram whereas you say you can actually boot the hard drive....

I think the fail-ness is more of a symptom of the other OS and you confirming that linux runs off the same drive seems to fall into place.

This thing can not even run the Windows setup cd though-- it hangs when the mouse appears.




Check your error logs (#tail dmesg) and look for hard drive errors like I get with the livecd. I bet, if you feel like experimenting, that if you wipe out Windows or format the drive in linux you will have a working drive.

---

### Post by Mordac85 on 2008-08-04
It won't matter if it truly is a drive failure.  Best thing to do to save time w/Dell support is download the diagnostics and boot to them to run them against your system.  Don't rely on the diagnostic partition especially if you think the drive is bad.  Run the quick tests first to cover everything and then go into detail on the drive or any other item that gives an error.  Make sure you write down exactly what the errors are and note any beep codes, SMART errors or any other indications of a problem.

---

### Post by subzero27 on 2008-08-06
Can you tell us what was the particular error code that you got.....i don't think ubuntu ate up your disk,it may be that your mbr is getting corrupted.

do a check with a third party utility and you will know....

---

