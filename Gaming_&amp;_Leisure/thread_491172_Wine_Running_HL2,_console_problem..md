---
title: "Wine Running HL2, console problem."
date: 2007-07-03
forum: Gaming &amp; Leisure
---

### Post by Kirby Sticks on 2007-07-03
[[IMG]http://img520.imageshack.us/img520/6383/screenshotss2.th.png[/IMG]](http://img520.imageshack.us/my.php?image=screenshotss2.png)
The text within the game console is practically unreadable, i searched around the forums and outside sources but i can't find a solution.  Any clues on how to fix this problem?  Thanks in advance because as soon  i post this i'm going to bed.  I've been up for about 20 hours. :KS

Also this isn't a mod thing, this is universal with all of the hl2 games.

Edit: Added some info.

---

### Post by Sockerdrickan on 2007-07-03
mstt corefonts or whats its called  :) google it and then apt-get install -it

---

### Post by Kirby Sticks on 2007-07-03
I've installed the core fonts and even copied them to /.wine/drive_c/windows/fonts but alas, it doesn't work.  Thanks anyway, unless somebody knows the EXACT fonts that the console uses?

---

### Post by Kirby Sticks on 2007-07-04
Does no one else have this problem?  I've installed the core fonts but that doesn't work.  I admin a few servers and i have to be able to read the console to properly administrate them.

---

### Post by Sockerdrickan on 2007-07-10
I have the same problem but it doesn't bother me

---

### Post by cogadh on 2007-07-10
I think the font the console uses is the Tahoma font. That font isn't part of the msttcorefonts package. Just download it or copy it off a Windows machine and put it in Wine's font folder.

---

### Post by Brynster on 2007-07-10
its a font rendering issue, not the lack of fonts installed.

If you don't install the msttcorefonts it looks exactly the same as when you do. Therefore its NOT a font issue.

The font used by Valve inside steam and its console is Tahoma. Until Wine fixes a rendering issue the font will always look like that

---

### Post by Sockerdrickan on 2007-07-10
Ok. ;)

---

