---
title: "No sound in Flash."
date: 2005-06-11
forum: Desktop Environments
---

### Post by Chrisb319 on 2005-06-11
I can get the flash to play but I can't get any sound to play.

---

### Post by kvidell on 2005-06-11
[QUOTE=Chrisb319]I can get the flash to play but I can't get any sound to play.[/QUOTE]
 Is this with the flash player from the repositories?
I think I had that problem too. I went to the official FireFox Plugin site and downloaded the flash player from there, installed it, and haven't had a problem since.

Something to think about :)
- Kev

---

### Post by Toddy on 2005-06-12
To add sound to flash:

sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1

restart firefox

---

### Post by bailey_ca on 2005-06-21
[QUOTE=kvidell]Is this with the flash player from the repositories?
I think I had that problem too. I went to the official FireFox Plugin site and downloaded the flash player from there, installed it, and haven't had a problem since.

Something to think about :)
- Kev[/QUOTE]
Though this is the Warty forum, I was having the same problems with Hoary. Turns out other people were too: Toddy, who replied before I could, and [https://wiki.ubuntu.com/SoundProblemsHoary](https://wiki.ubuntu.com/SoundProblemsHoary).

---

