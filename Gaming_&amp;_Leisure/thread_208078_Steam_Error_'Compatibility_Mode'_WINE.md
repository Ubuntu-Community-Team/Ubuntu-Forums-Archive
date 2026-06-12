---
title: "Steam Error 'Compatibility Mode' WINE"
date: 2006-07-03
forum: Gaming &amp; Leisure
---

### Post by sudopimp on 2006-07-03
I have installed steam, but when I start Steam.exe in my fake c drive, program files, is comes up with a pop up saying

-----------------------------------------------------------

Please turn off 'compatibility mode'.

-right-click Steam.exe
-Select properties
-go to 'compatibility' tab
-un-check 'Run this application in Compatibility mode'


------------------------------------------------------------

but there is no compatibility tab

any help would be greatly appreciated

thank you very much in advance

---

### Post by Indras on 2006-07-03
The instructions that it is giving back to you are how to turn off compatibility mode in windows... since you're in Ubuntu running wine, they won't work.  Wine has its own compatibility mode.

Run winecfg, and in the Applications tab, there's a drop box to select the version of Windows that Wine will try to emulate.  I suggest selecting Windows XP, but if that doesn't work, perhaps Windows 2000 or 2003 might.

I've never used steam before, so I can't give you any application-specific help, I can only tell you what I know from playing around with wine.

---

### Post by sudopimp on 2006-07-03
i set it XP and it works!
but...
it stops at about 26% while updating

any ideas?

---

### Post by Indras on 2006-07-04
I can only refer you to the Wine entry for Steam (like I said, I don't own it and have no experience with it, even in windows):

[http://appdb.winehq.org/appview.php?versionId=1554](http://appdb.winehq.org/appview.php?versionId=1554)

---

