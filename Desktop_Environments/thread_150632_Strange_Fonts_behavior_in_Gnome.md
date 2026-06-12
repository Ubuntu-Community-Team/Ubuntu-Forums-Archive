---
title: "Strange Fonts behavior in Gnome"
date: 2006-03-26
forum: Desktop Environments
---

### Post by LacteuS on 2006-03-26
Hi,

I'm currently on Dapper, but I had this problem with Breezy, before I dist-upgrade, and the problem is stilling there...

This is a font size problem, like a lot of fonts problems, but after searching as longer as I could, I didn't found any clue...

When I boot the X server, GDM, then Gnome, the font size is correct everywhere, but not in the title bar (of all app, I use XGL/Compiz). Fonts size in software like Firefox, or OOO are not correct, as you can see on this screenshot.

[IMG]http://lacteus.free.fr/public/font/small_font.png[/IMG]
[IMG]http://lacteus.free.fr/public/font/font_config.png[/IMG]

If I start the gnome-font-properties app (System -> etc.), and if I launch again Firefox or OOO, the size is correct ! (else in the title bar :( )

[IMG]http://lacteus.free.fr/public/font/normal_font.png[/IMG]

So, there is a config at Gnome start-up which is not correctly loaded (or there is another config loaded, which doesn't match with the gnome-font-properties config). But which one ???

I have used switch and switch2 app a couple month ago, when I tried e17.

Thanks :)

---

### Post by LacteuS on 2006-03-27
Up :)
Nobody has an idee ?

---

### Post by LacteuS on 2006-04-02
The problem were in the .Xdefaults file :)
I've changed this line :
Xft.dpi: 75
to this :
Xft.dpi: 96

Et voilà ! :D

---

