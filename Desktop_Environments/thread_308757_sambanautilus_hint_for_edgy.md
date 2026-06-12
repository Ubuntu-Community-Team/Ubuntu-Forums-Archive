---
title: "samba/nautilus hint for edgy"
date: 2006-11-28
forum: Desktop Environments
---

### Post by carlosK on 2006-11-28
Hi all,

I've been experiencing issues with browsing samba shares from nautilus; computers would show up as blank icons, requiring numerous refreshes (F5) before they would display correctly.

This behavior now appears to be fixed.  The solution I found was to use gconf-editor and add the name of my windows workgroup to the following entry:

/system/smb/workgroup

I hope this helps anyone else experiencing problems with nautilus and samba.

carlos
--

---

### Post by Baptiste on 2006-12-18
Thanks for all! It fixed the problem. However, you should file a bug on launchpad if you did not make it yet. It would be useful for people who don't know this tip! It was really a very annoying bug.

---

### Post by tagra123 on 2007-01-03
I posted a similar solution.   It does appear to be a bug. My solution also lets windows resolve the share correctly too.

[http://www.ubuntuforums.org/showpost.php?p=1960858&postcount=18](http://www.ubuntuforums.org/showpost.php?p=1960858&postcount=18)

---

