---
title: "I packaged Ularn for Ubuntu"
date: 2009-09-18
forum: Gaming &amp; Leisure
---

### Post by themcp on 2009-09-18
Hi all. I've built .deb packages for Julian Olds's excellent update of the classic roguelike game Ularn (1.6.3a). 

You can grab them [**here**]("http://www.kitmalone.com/ularn/").

It's my first try at making .deb packages, so let me know if you have any trouble!

---

### Post by Grishka on 2009-09-18
cool. thanks. I'm getting 'can't read scoreboard', for some reason, but apart from that, everything looks fine so far.

---

### Post by themcp on 2009-09-18
whoops - forgot to set permissions for the score file.

"chmod a+w /usr/lib/ularn/Uscore" oughtta do it.

I'll get a fix posted sometime this afternoon.

---

