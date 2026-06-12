---
title: "[SOLVED] Xfce:  	
&amp;quot;Other&amp;quot; category in menu is called &amp;quot;kspace %d&amp;quot;"
date: 2006-11-17
forum: Desktop Environments
---

### Post by rrwo on 2006-11-17
In Xfce, the Settings Manager icons were labelled "Button Label|Desktop", etc.  I was given a fix on the Xfce forums, [http://forum.xfce.org/index.php?topic=2676.0](http://forum.xfce.org/index.php?topic=2676.0)
but a new problem has cropped up, which may or may not be related:
the Xfce menu is garbled. The "Other" option is called "kspace %d", with a submenu "b>" that contains the items originally in Other.
Undoing the changes to the mangled Settings Manager labels and rebooting does not erase this problem, so I'm not sure if there is a connection.

I had this problem with Ubuntu 6.06, but after upgrading to 6.10 it went away for a short while. After fixing the same issue with the Settings Manager button labels, the kspace issue came back.

Any idea how to fix this?

(Note: this issue has also been asked on the Xfce forum, [http://forum.xfce.org/index.php?topic=2933.0](http://forum.xfce.org/index.php?topic=2933.0))

A screenshot is below.

---

### Post by videodrome on 2006-11-19
Is it possible to locate and delete the offending file in user/share/applications ?

Do any of these links help?
[https://xubuntu.wordpress.com/2006/08/04/howto-remove-menu-entries-from-the-system-menu/](https://xubuntu.wordpress.com/2006/08/04/howto-remove-menu-entries-from-the-system-menu/)
[http://xubuntu.wordpress.com/2006/07/12/manually-edit-the-xfce-menu/](http://xubuntu.wordpress.com/2006/07/12/manually-edit-the-xfce-menu/)

---

### Post by rrwo on 2006-11-19
I tried ```
grep kspace *
``` from within /usr/share/applications. Nothing matches, so I don't think the problem is related to broken *.desktop files.

---

### Post by rrwo on 2006-12-16
I upgraded to Xfce 4.4 RC2 (from Xfce's website), and this seems to have fixed the problem (for now, anyway).

---

### Post by rrwo on 2007-02-08
Problem came  back, but upgrading to the final 4.4.0 release seems to have fixed it. I've been using it for weeks and the problem has not recurred.

---

