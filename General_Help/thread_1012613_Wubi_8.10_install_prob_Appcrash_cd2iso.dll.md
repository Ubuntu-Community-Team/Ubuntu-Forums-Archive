---
title: "Wubi 8.10 install prob: Appcrash cd2iso.dll"
date: 2008-12-16
forum: General Help
---

### Post by Ashin Sopaka on 2008-12-16
Posted this in another thread, but since it is Wubi specific, thought to post here as well - forgive the lack of netiquette is this is improper :)

Downloaded Ubuntu, extracted to DVD. Used Wubi download from their site as well as the one bundled with the Ubuntu d/l. Installing on C:/ drive (where Windows Vista Ultimate is located) and getting the following message:


Problem signature:
Problem Event Name: APPCRASH
Application Name: wubi.exe
Application Version: 8.10.0.515
Application Timestamp: 4878f22c
Fault Module Name: cd2iso.dll
Fault Module Version: 0.0.0.0
Fault Module Timestamp: 4905fb73
Exception Code: c00000fd
Exception Offset: 00007ceb
OS Version: 6.0.6000.2.0.0.256.1
Locale ID: 2057
Additional Information 1: 8d13
Additional Information 2: cdca9b1d21d12b77d84f02df48e34311
Additional Information 3: 8d13
Additional Information 4: cdca9b1d21d12b77d84f02df48e34311

Using a Sony FZ27G, 32 bit.

Any suggestions? Thanks in advance.

---

### Post by ago on 2008-12-16
Use wubi.exe directly with the ISO. Place both in the same folder. Also use the CD Desktop ISO, not the DVD one.

---

### Post by Ashin Sopaka on 2008-12-19
That did it! Thanks so much!

---

