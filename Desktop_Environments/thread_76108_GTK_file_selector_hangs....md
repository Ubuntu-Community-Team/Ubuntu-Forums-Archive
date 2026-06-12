---
title: "GTK file selector hangs..."
date: 2005-10-14
forum: Desktop Environments
---

### Post by Liam on 2005-10-14
I've been having really aggravating problems with the GNOME file selector dialog for awhile now. It started happening in 2.10 on Hoary, but it's even more frequent in Breezy.

Basically, whenever I attempt to access the file selector from any application to either open or save a file, it'll hang the application (abiword, firefox, etc), and occasionally freeze the panel. I'll have to manually kill the process, and restart GDM if the panel gets hung up.

There appears to be no rhyme or reason to it. When I start the process from a terminal, I don't get any errors, just a hang.

It never seems to happen with the handful of Qt apps I use.

Anybody have any idea what gives?

Thanks.

---

### Post by Liam on 2005-10-14
I should probably add that I dist-upgraded.

---

### Post by Megatog615 on 2007-07-14
I know this is FREAKISHLY OLD and I'll probably be flamed for this.

I have had this problem for as long as I can remember. It has spanned multiple distributions and has prevented me from using applications like Firefox and GIMP, both of which use the GTK file open dialog.

---

### Post by timseal on 2007-12-04
Me too.  I found this (obviously unhelpful) thread while desperately searching for a tweak or something to speed it up.  Some people complain about the interface, well I don't care, it just takes so bloody long to do anything that I hate it, hate it, hate it!

---

### Post by ktulu1115 on 2008-05-03
I'm noticing this problem for the first time on a clean Hardy install myself...  can't seem to figure out the problem, driving me nuts.

Firefox/gedit/etc hangs for about 20-30 seconds whenever the GTK file selection dialog window appears, then it comes back OK.  Anyone else have this issue on Hardy?

---

### Post by dustingram on 2008-05-08
I'll second that, I'm having the problem any time I open the file browser with Firefox, GIMP, etc, whether it is to open a file or save one.

Anyone have a solution?

---

### Post by ktulu1115 on 2008-05-09
I'm fairly certain that it has something to do with compiz and when disabled, the issued disappears.  I have yet to re-enable it to see if it'll come back.

Also think the problem disappeared as a different user, but again, have yet to confirm.  Anyone else come up with anything more yet?

---

