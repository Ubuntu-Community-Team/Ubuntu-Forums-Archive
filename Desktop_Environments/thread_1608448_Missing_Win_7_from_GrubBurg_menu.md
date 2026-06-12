---
title: "Missing Win 7 from Grub/Burg menu"
date: 2010-10-29
forum: Desktop Environments
---

### Post by JohnH on 2010-10-29
I have spent MANY hours trying to recover a Win 7 entry in both Grub and later, Burg. I was losing this off the menu (I think after a kernel update) and it would not appear after a reinstall of Grub (or Burg).

Solution: Following a variation of an idea I saw in Sourceforge [HTML]http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Core_On_Windows[/HTML]I went to the Windows partition from Ubuntu (which was booting okay) and found **two** /boot folders in that partition: one written in caps (/BOOT)and the other in lower case (/boot). I deleted the one with residual grub info, (i.e. the one with lower case), keeping the folder with Windows info (BCD etc) intact. 

I rebooted and Windows 7 appeared on my Menu again.

I hope this might help someone and save many hours of installing and reinstalling of MBR/Grub stuff.

Regards
John

---

