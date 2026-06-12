---
title: "Nautilus copy file/directory path should not put &quot;file://&quot; prefix"
date: 2010-12-27
forum: Desktop Environments
---

### Post by hadaxu on 2010-12-27
I really missed the old Ubuntu file/dir. copying feature. When I copied in nautilus file explorer and paste into a terminal or text editor, I got the exact path (eg. /home/user/abc.txt), but when coming the Ubuntu 10.04, it added some "file://" prefix to the actual path (eg. file:///home/user/abc.txt), and I always had to manually delete the "file://" prefix.

I don't see clearly that we need to place "file://" in front of the actual path (maybe just in the case we want to put the path in an Internet browser?). Wish this reversed back.

---

### Post by deadimp on 2011-09-27
I wholeheartedly agree with this.
However, when I copy / paste from Nautilus into another application, such as GEdit, it does not include the GVFS protocol prefix.
This only occurs when pasting into the terminal - which is still counter-intuitive.

Could it be something with the terminal and GVFS itself?


EDIT: Found this: [http://forums.debian.net/viewtopic.php?f=10&t=62310](http://forums.debian.net/viewtopic.php?f=10&t=62310)

If you copy a file and then go to the 'Edit' menu on gnome-terminal, there will be a 'Paste Filenames' option, which pastes it with quotes - but apparently there's no custom keyboard mapping :/ (aside from Alt + E + F).

---

### Post by hadaxu on 2011-10-28
Alt+E+F is way better than pasting in Gedit and re-copy, or manually remove the file:// prefix, but still not the best. Thanks.

---

