---
title: "&quot;gksudo&quot; Compiz Fusion Troubles"
date: 2007-07-14
forum: Desktop Effects &amp; Customization
---

### Post by LancerDragoon on 2007-07-14
Hey, guys.

Like the title of this post says, I'm having some problems with gksudo while running Compiz Fusion. The problem happens whenever I need to enter a password to do administrative tasks, not just running a command like gksudo gedit <filename> or the like. After I enter my password, my computer hangs and I can't do anything except CTRL+ALT+Backspace. 

Anybody know why this is and can it be fixed?

---

### Post by Songwind on 2007-08-25
I got this error today for the first time.

---

### Post by Songwind on 2007-08-25
And, I found a work around *and* a possible solution [over at the Compiz forums]("http://forum.compiz-fusion.org/showthread.php?t=2250&highlight=gksudo")

---

### Post by outphase on 2007-08-25
There's a workaround posted elsewhere in the forum for those who have had this problem for longer. My nVidia based desktop doesn't have problems, but my Intel based notebook does.

gconf-editor
apps, gksu
check the box for "disable-grab"

It says it's slightly insecure, but it's better than crashing.

---

