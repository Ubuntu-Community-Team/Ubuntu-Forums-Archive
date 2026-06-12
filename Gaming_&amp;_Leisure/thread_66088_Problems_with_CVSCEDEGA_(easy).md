---
title: "Problems with CVSCEDEGA (easy)"
date: 2005-09-16
forum: Gaming &amp; Leisure
---

### Post by MrSt0ne on 2005-09-16
Hi, whenever i try to install starcraft using cvscedega install.exe i get this error:

For language 'en' several language ids were found:
en_US - 0409; en_GB - 0809; en_AU - 0C09; en_CA - 1009; en_NZ - 1409; en_IE - 1809; en_ZA - 1C09; en_JM - 2009; en_ - 2409; en_BZ - 2809; en_TT - 2C09;
Instead of using first in the list, suggest to define
your LANG environment variable like this: LANG=en_US
err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
ALSA lib seq_hw.c:446:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
wine: Unhandled exception, starting debugger...

i dont know how to use the debugger, and im new to linux. Please help me

---

### Post by Caboto on 2005-09-16
I've got the same problem, but with Steam. Whenever I start Steam, I see the Login Window but without any text. I've tried to copy some fonts to the named location, but it still doesn't work.

Have you got a similar problem or is cvscedega just killed completly?

---

### Post by krak on 2005-09-16
[http://transgaming.org/forum/viewtopic.php?t=3113&highlight=enus](http://transgaming.org/forum/viewtopic.php?t=3113&highlight=enus)

this should help

---

### Post by MrSt0ne on 2005-09-16
ok, im still having the problem. Can someone set me up with a walkthrough? Im getting this error still and it shuts it down completely, and I cant run my Starcraft Setup, its Depressing:

joshua@ubuntu:/media/cdrom$ cvscedega setup.exe
err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
/home/joshua/.WineCVS/installs/cvscedega/bin/wine: binary overlaps reserved area (08048000-0804ca1c)
joshua@ubuntu:/media/cdrom$ err:font:ReadFontDir Can't open directory "/usr/X11R6/lib/X11/fonts/truetype/"
ALSA lib seq_hw.c:446:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
wine: Unhandled exception, starting debugger...

and it just quits. Please help, it would be greatly appericated!

---

### Post by krak on 2005-09-17
i had same problem some time ago but dont remember how i have solve it.. ;(

---

