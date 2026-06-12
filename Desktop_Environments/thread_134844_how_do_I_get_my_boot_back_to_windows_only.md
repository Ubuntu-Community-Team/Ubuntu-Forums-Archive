---
title: "how do I get my boot back to windows only ?"
date: 2006-02-22
forum: Desktop Environments
---

### Post by HarryMangurian on 2006-02-22
I need to uninstall Breezy from one of my machines.  This will leave me with Windoze XP as the only OS on this computer.  What is the proper way to do this so that I will be able to boot to Windows ?


thanks in advance,

---

### Post by cskeide on 2006-02-22
You should be able to boot into a "rescue mode" with your WinXP CD. From there you can restore your master boot record with "fixmbr".

If that works you can just delete the ubuntu partition from windows, using for example partition magic.

---

### Post by OpticalIllusion on 2006-02-22
You can just delete the Ubuntu partition using the Windows XP installation disc.  It works fine.

---

### Post by hyper84 on 2006-02-23
I have used the "fixmbr" method mentioned above many times before to save my computer when I was first learning (by myself) to install and use linux.

---

