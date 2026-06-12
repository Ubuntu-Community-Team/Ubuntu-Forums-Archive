---
title: "AVG for Ubuntu: necessary or just bad?"
date: 2009-02-07
forum: General Help
---

### Post by Tienshinan8 on 2009-02-07
I downloaded and installed AVG for Linux, but I haven't scanned my system yet.  My main fear is false positives.  I have AVG free for Windows and it works nicely.  My questions are:

Would it be as easy to restore files falsely identified as viruses as it is in the Windows version?

Should I enable heuristics?

Or should I even have this on Ubuntu (Hardy) in the first place?

---

### Post by AoA Linux on 2009-02-07
I have AVG running in Ubuntu 8.10 and it has never reported any viruses, you are not very likely to get a virus anyway.  To answer your first question, I have never had it identify any viruses so I do not know the answer to this one, but to your last question it is more of a peace of mind thing.  If you want to MAKE SURE you system is secure though, I recommend the UFW firewall you can download from the Add/Remove under applications if you have not already done so.

---

### Post by SunnyRabbiera on 2009-02-07
Such a thing is practically useless, as Linux doesnt have viruses or at least ones that really work and do actual harm.

---

### Post by gjoellee on 2009-02-07
If you god a virus it has to be designed for Linux, but I don't think Linux allows operations to be launched without a users permissions. Therefor does viruses have to be launched manually!

---

### Post by Tienshinan8 on 2009-02-07
Thanks.  :)

---

### Post by MartyBuntu on 2009-02-07
I think anti-virus is to scan for virus that might be shared on a network with Windows machines.

I wish people would stop saying there's no need for virus monitoring software in Linux.

---

### Post by mb_webguy on 2009-02-07
I very rarely see anyone saying that there's no need for virus scanners on Linux, but I quite often see people saying that there's no need for virus scanners on Linux *for desktop users who aren't dual-booting with Windows*, which is pretty much true.  Linux webservers and mailservers need virus scanners to avoid passing on viruses to clients, and people who dual-boot with Windows could use a virus scanner to avoid passing a virus to their Windows installation (though they should also be running antivirus software in Windows, of course), but otherwise there's not much point.

While there have been a handful of Linux-based viruses in the past (as opposed to hundreds of thousands of known Windows-based viruses), none of them were anywhere near as virulent as Windows viruses, and none can infect current Linux systems, since the vulnerabilities they utilized have been patched.

As to the original post:  I did have AVG for Linux installed because I like the Windows version, but I've recently switched to using ClamTK (a GUI front-end for clamav).  AVG for Linux is purely a scanner, and has no ability to quarantine infected files, while ClamTK can.  I also noticed some bugs in AVG for Linux where the window wouldn't display properly and scans wouldn't start.  ClamTK, on the other hand, is very solid.

---

### Post by hyper_ch on 2009-02-07
AV on linux is not needed... as the previous poster says, if you run public email/file server you may want to run it (also because of liability questions) however I think if someone doesn't protect themselves they will get infected anyway and the chance that it's me who's infecting them is very slim and if I don't infect them, someone else will.

---

