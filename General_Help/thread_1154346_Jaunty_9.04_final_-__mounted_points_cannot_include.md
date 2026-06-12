---
title: "Jaunty 9.04 final -  mounted points cannot include escape characters"
date: 2009-05-09
forum: General Help
---

### Post by bobwyajnr on 2009-05-09
Hi folks,

I have quite a number of external harddisks hooked up via SATA PM's to my server box. These harddisks are formatted NTFS and have volume labels with ' ' and '(' / ')' characters in them. In previous incarnations of Ubuntu (8.04 and 8.10) these drives would mount with the same path as the label. Great just what I wanted! I don't care if I have to escape a few characters on the command line - Linux is not DOS so has always supported spaces and brackets in the path!!

Now with Jaunty 9.04 it seems to be impossible get the drives mounted without them being ISO-ified!! So all the escaped characters are replaced by '_' underscores... This makes my mounted drives much less readable on the desktop and annoys the **** out of me!! Is there anyway to stop this happening??

Instead of:
```
/media/S 1Tb (02)/
``` (= Samsung 1Tb (02))

I get:
```
/media/S_1Tb_02_/
```

Bob

---

