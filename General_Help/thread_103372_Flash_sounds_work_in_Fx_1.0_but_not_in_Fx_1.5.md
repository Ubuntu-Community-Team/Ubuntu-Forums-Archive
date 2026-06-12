---
title: "Flash sounds work in Fx 1.0 but not in Fx 1.5"
date: 2005-12-14
forum: General Help
---

### Post by amokoura on 2005-12-14
I can't get the Flash sounds to work in Firefox 1.5. I've tried every possible trick mentioned here without any results. The only hint for the problem is that the **Flash sounds work ok in Firefox 1.0** :???:

---

### Post by stuporglue on 2005-12-14
I have had trouble with Flash in the newer Firefoxes also. I ended up just using Macromedia's downloadable installer. Once I used that, it "just worked" on every install and FF version I've tried so far (all x86). I've done it on about 8 or so different computers.

---

### Post by amokoura on 2005-12-14
[QUOTE=stuporglue]...I ended up just using Macromedia's downloadable installer...[/QUOTE]

I downloaded it and tried to install to /usr/lib/mozilla and /usr/lib/mozilla-firefox. Didn't help. Thanks anyway..

Maybe I should just wait for the backport then,

---

### Post by mikkelwe on 2005-12-14
Install it to ~/.mozilla/plugins or install it system wide in /path/to/firefox-1.5/plugins (substituting with the actual path to firefox-1.5, of course).
By the way, firefox-1.5 will probably never be in backports since it would break more than 50 programs that rely on gecko and stuff. Read [http://distrowatch.com/weekly.php?issue=20051212#3](http://distrowatch.com/weekly.php?issue=20051212#3) for reference.

---

