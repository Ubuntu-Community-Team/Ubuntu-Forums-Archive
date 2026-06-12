---
title: "Nautilus crashes when opening some files"
date: 2009-06-09
forum: General Help
---

### Post by legatek on 2009-06-09
Hi all, I've been having a problem for the past couple of days with Nautilus crashing. It appears to happen when I try to open some files (for example, a .svg, a .tif or a .pdf, but not all examples of these file types). If I double click on these files, or open the "open with..." dialogue the window becomes non-responsive, and I can then use the open window as an eraser to remove my desktop icons. I have to kill nautilus and start it again to return things to normal, but if I try to open these files again the problem is reproduced. I can open these files from within an application, so the files themselves are not corrupted. For the first occurrence after logging in, the following appears in my .xsession-errors file:

```
X Error of failed request:  167
  Major opcode of failed request:  153 (DAMAGE)
  Minor opcode of failed request:  3 (XDamageSubtract)
  Serial number of failed request:  248357
  Current serial number in output stream:  248358
```

Subsequent occurrences after restarting nautilus give no additional error messages.

These files are on a NTFS-formatted drive, and I booted into Windows to run chkdsk /F and defragment the drive (which needed doing anyway) but this didn't solve the problem. Does anyone have a suggestion for what else I can try?

---

### Post by Soul-Sing on 2009-06-09
the only relevant thing/topic I found: [http://ubuntuforums.org/archive/index.php/t-419288.html](http://ubuntuforums.org/archive/index.php/t-419288.html)

---

### Post by legatek on 2009-06-10
*bump*

I haven't made any changes to my xorg.conf file, so the above thread doesn't apply.

---

