---
title: "Anyone having Trash crash or file permission problems?"
date: 2009-02-03
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Rallg on 2009-02-03
I am a moderately knowledgeable user, with Dell mini 9, 2G memory, no swap, 16G storage, Bluetooth (unused), no webcam. This computer came with XP, which I later removed then installed Ubuntu 8.10 (directly from Ubuntu, not Dell). Everything is upgraded to now. No reason to think that the system has malware.

Within the last few days, I have had some occasional, severe problems. Generally, they seem to be related to file system integrity. In some cases, files have had permissions changed for no apparent reason. In other cases, the file system check showed numerous errors that had to be fixed.

I've had the computer since October 2008, and used it a lot. Still, I would not think that I have worn out the solid-state storage yet!

After various checks and changes, I am wondering if there is something odd with the Trash applet. For example, just recently it refused to delete a handful of desktop documents (nothing unusual), and the WiFi immediately crashed. No more WiFi until reboot.

Has anyone else seen this kind of behavior? I searched, but did not locate anything obvious (such as a known Trash bug).

---

### Post by jimv on 2009-02-04
Just to be safe, I'd run memtest86 and fsck on your filesystem.  Bad ram or a defective HD could cause behavior like you are seeing.

---

### Post by Rallg on 2009-02-04
Indeed, after each problem, fsck (run from another Ubuntu on USB drive) reveals numerous drive problems. This computer uses solid-state drive rather than disk. Solid-state drive supposedly has less lifetime, but I wouldn't think it would be that short. RAM is OK.

Further info: I have realized that it is not Trash that is causing other things to crash, but apparently it is the WiFi causing a crash (that may not be obvious until something else is opened). Also, it seems to depend on where I do the WiFi. Same problem with the original 8.10 driver and the restricted driver.

As far as I can tell, some kind of burp in the WiFi creates an error that propagates through the system, either via memory or via corrupted files. It can be fixed via fsck, provided that I get away from the problematic WiFi transmitter. Understand that the same WiFi did not previously cause problems on Windows, and is not reported as problematical by other Windows or Mac users.

This gives me the impression that some sort of error in the WiFi transmission, which ought to be disregarded by my computer, instead forwards corrupted data to my system. if that is the case (and I am not at all sure it is the case) then it is a problem with both the standard and restricted WiFi drivers, or with network manager, for this system. The Dell mini 9 uses an Atom processor, rather than Pentium. Could that be the problem?

The latest wierdness: After crash at WiFi location A, and system correction via fsck, I went to WiFi location B. Not problem there, BUT my theme had been changed!

Of course, if I had crash logs or bug reports, I would file them.

---

### Post by jimv on 2009-02-05
Hmmm..that's so weird.  The first thing I would do is trying a different wireless driver, in this case, Ndiswrapper with the Windows version of the driver.

---

### Post by Rallg on 2009-02-05
I might try the ndiswrapper route. However, I should point out that the WiFi wasn't giving me troubles before. Either I have a hardware problem, or something is odd in the software. The problems persist. I have not been losing data, but various setting seems to change.

What I will do today is deactivate the WiFi and use cable on a known-good network. That will determine whether or not the WiFi is really involved, or not.

In any case, since I'm the only one reporting this behavior, and I hadn't seen it before, it doesn't sound good. :(

---

### Post by jimv on 2009-02-05
It sucks to be the first when it comes to software problems.

---

### Post by Rallg on 2009-02-08
The more I look at this, it seems to be the case that when my WiFi gets an erroneous signal from the transmitter (maybe due to weak signal, noise, or interference from other nearby transmitters) it does not discard the erroneous input, but propagates it to the system, causing havoc.

This seems to be true whether the driver is the 8.10 included driver, or the proprietary driver. I.ll forget about ndiswrapper for now.

I never had a similar problem with my other computer, which is a different model from Dell (presumably uses different WiFi hardware).

So, if I am in a "good location," no problem. If I am in a "bad location," big-time problems. No others (using their Windows or Mac) have any difficulty in the same area. I don't have a problem with my other computer, using Ubuntu but different hardware.

Unfotunately, I have no crash reports and logs, or I would submit a bug report.

For now, I advise others that if your Dell mini 9 (originally Windows, now Ubuntu) occasionally goes berserk, it may be that you need to find a different WiFi location. Apparently there is a noise rejection problem, or bad files are not properly checked before being passed to memory for processing?

---

