---
title: "[SOLVED] SANE-DLL problem ?"
date: 2008-09-06
forum: Desktop Environments
---

### Post by gusteman on 2008-09-06
Hi there, Community,
I recently installed a new printer HP Deskjet F4180 All-In-One. First of all I couldn't get it running, but after upgrading from Feisty to Gutsy that problem was solved. Except for the scanner. SANE doesn't seem to recognize it, anyway I can't find the **libsane-dll.a** file in the SANE directory. And it should be there according to **man sane-dll**. Any suggestions :confused: Thanks a lot :)

---

### Post by bmac on 2008-09-07
Have you installed the HP print driver?

[http://hplip.sourceforge.net/downloads.html](http://hplip.sourceforge.net/downloads.html)

After installing this driver all functions of my hp all-in-one printer/scanner/fax worked without any other mods.

Hope this helps.....

---

### Post by gusteman on 2008-09-07
@ BMAC
Thanks a lot for the link and the suggestion. As it did for you, it worked for me!!!
I must say that I tried this solution under Feisty but there it did not work. So I upgraded to Gutsy and I found that HPLIP was embedded in Gutsy so I did not try out this solution. Well, now it looks like I should have.
Anyway, once again thanks for the support.
I have learned another lesson: if at first you don't succeed, try, try, try again!

---

### Post by bmac on 2008-09-07
Glad you got it working.

Don't feel bad as I did the exact same thing.... Finally, figured I'd try the new version from Source Forge and it worked...

Good Luck..

---

