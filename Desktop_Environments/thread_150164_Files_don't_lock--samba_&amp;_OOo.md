---
title: "Files don't lock--samba &amp; OOo"
date: 2006-03-25
forum: Desktop Environments
---

### Post by dgermann on 2006-03-25
The problem: Two users can have the same OOo file open at the same time, and both edit it. The last one to save the file wins!

The system: 3 Ubuntu 5.10 client boxes and one WinXPPro client box, all running OOo 2.0; one server with RedHat 9.0 running samba version 2.2.7a-security-rollup-fix.

Did some further testing and found that I could gedit a file at the same time on both computers, too. Trying to vi the same file on both produced an error in vi, either at the opening of the file or at the saving. But KWord could have a file open and edit it when it was open and being edited in gedit. This suggests to me that it is not wholly an OOo issue, although OOo might have an internal solution.

I tried this, hoping it would be solved by OOo--
 export SAL_ENABLE_FILE_LOCKING=1
but it made no difference. Even did another one changing STAR for SAL, and no difference either.

So, got any ideas how to trouble shoot this?

Thanks!

---

