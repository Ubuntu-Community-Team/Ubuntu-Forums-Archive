---
title: "HP Photosmart Premiun"
date: 2009-05-04
forum: General Help
---

### Post by MrBungle79 on 2009-05-04
Hi all,

I have just made the jump to ubuntu from wi#$@*^ws and so far love it!  I have purchased a HP C309 Photosmart Premium printer/fax/scan/copy.  The printing worked first time, but the scaning wont.  Any Clues?

Thanks.

---

### Post by MrBungle79 on 2009-05-04
got it sorted, thanks.

---

### Post by cssutto on 2009-08-06
I just purchased the same printer and I can't get it to scan either, using either Gump or Xsane.

Could you give me a clue?

CSSJR

---

### Post by Returner on 2009-09-26
To use most features of the HP Photosmart c309, I installed by using the terminal:

```
sudo apt-get install hplip-gui
```

Then in the System Menu, that HP-toolbox Icon appears in B/W, which gives you most controls over your MFC.

---

### Post by alfitch0619 on 2009-12-20
Try this.  It is the latest version of HPLIP and it solved all problems.
[http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)

---

### Post by steveneddy on 2009-12-20
> **alfitch0619 said:**
> Try this.  It is the latest version of HPLIP and it solved all problems.
[http://hplipopensource.com/hplip-web/downloads.html](http://hplipopensource.com/hplip-web/downloads.html)

This is the correct answer. The version of HPLIP in the repos is hobbled. The version at HP's website will make your HP printers print, scan and fax and will also let you keep track of ink levels.

---

