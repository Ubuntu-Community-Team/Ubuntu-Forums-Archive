---
title: "Steam fonts issue"
date: 2006-12-09
forum: Gaming &amp; Leisure
---

### Post by Lystrodom on 2006-12-09
So I've gotten Steam to install and such, but I can't read anything. I have the Tahoma.ttf file in the correct wine folder, but it still doesn't do anything. I even tried two different Tahoma.ttfs.

Any ideas?

By the way, I'm running Edgy, if that makes a difference.

---

### Post by Lystrodom on 2006-12-10
Bump, anyone?

---

### Post by Brynster on 2006-12-11
when you you have the fonts in the right folder, can you elaborate a little (ie give use the path details).

---

### Post by DUNC4N on 2006-12-11
I'm having the same issue right now. I've installed steam, via wine. I now have an Icon on my desktop that says steam. when I double click it It starts but i can't read anything. I know I need to install the tahoma.ttf font. I've downloaded two differnet(man I'm tired) ones on my desktop. I can't put those in the .wine/windows/fonts folder.

What am I doing wrong. 

Thanks.

---

### Post by willskills on 2006-12-11
Ok guys, if you manage to copy the Tahoma.tff to your ./wine/drive_c/windows/fonts and you still can't see anything. You might have been a doughnut and installed steam/wine as root?

In this case you also need to add the font to your /root/.wine/drive_c/windows/fonts

It might also be helpful to say, if you copied the two needed windows .dlls to your user/.wine folder, so should probably chuck the .dlls in the /root/.wine too.

---

### Post by Lystrodom on 2006-12-11
Amazing, that did it. Silly me and doing things as root.

---

