---
title: "Ubuntu Update Manager mangles menu.lst, loses kernel?"
date: 2005-09-07
forum: Desktop Environments
---

### Post by AndrewStout on 2005-09-07
In a quick search of the archives I've seen other posts complaining about this problem, but I didn't see any useful solutions (doesn't mean they're not there!)

I just did my first Ubuntu Update, which among other things ran an update on the kernel.  This did two mysterious and annoying things, and I'd like help with both:

1. the kernel update script or whatever it is runs grub-update [I observe], which mangles the menu.lst file I slaved over to get dual-booting working, among other things.  I infer that there is some automagic generation being done.
(a.) UBUNTU IN-CHARGE TYPES PLEASE NOTE: mangling users' menu.lst files without warning from an innocent looking update is a really bad idea.  I had to edit the entries at the GRUB command line in order to boot--and it's lucky that I learned how to do that last week.   [-X
(b.) I would really appreciate a pointer to some documentation on how the automagic processing of menu.lst is done, so I can play nice with it while still making the necessary or desired changes to my menu.lst.

2. I can't seem to find the new kernel images...the ones in my /boot directory are the same ones I had before [I think], so it looks like I've gotten my menu.lst blown away for nothing.  Where does the Ubuntu Update Manager put the new kernel, and where can I find a log of what the Update Manager did, so I could investigate this more systematically?

thanks in advance,
--Andrew

---

### Post by AndrewStout on 2005-09-07
[QUOTE=AndrewStout]
(b.) I would really appreciate a pointer to some documentation on how the automagic processing of menu.lst is done, so I can play nice with it while still making the necessary or desired changes to my menu.lst.
[/QUOTE]

[sheepishly]  so, `man update-grub' helps a little.  but only a little.

---

