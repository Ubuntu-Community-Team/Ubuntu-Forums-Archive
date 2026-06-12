---
title: "KWin as default window manager in GNOME"
date: 2009-04-27
forum: Desktop Environments
---

### Post by MariusLV on 2009-04-27
Hi all!

I love GNOME, but I also love KWin and its ability to display thumbnail previews even of minimized windows. As I find this feature quite useful I decided to replace Compiz with KWin in GNOME. This is easy enough in itself, but I have yet to find out how to enable it by default.

I made a workaround by making "kwin --replace" run as a startup script, but it is a very poor one. This method essentially involves loading metacity, only to replace it a second afterwards, which is silly enough in itself, but it also means that any program that depends on composition will refuse to load on startup. Specifically, this means I cannot have Docky (Gnome-Dos über-spiffy dock application) auto-start, but have to manually start it after KWin has loaded.

I realize mine is a bit of a luxury problem, but I was wondering still if anyone has a solution to this issue. Or perhaps I am the only one who feels the need to run KWin in GNOME?

Hope to hear from someone :-)
Thanks for reading!

---

### Post by Matt Brooks on 2010-11-28
If you go to gconf-editor by hitting ALT + F2 then typing "gconf-editor" without the quotes it should bring you to a configuration editor.

Go to: Desktop --> gnome --> applications --> window manager

Click on the entry for "default" and change it to the location of kwin (i havent tried but it will probably be /usr/bin/kwin).

Let me know if it works because id like to try. Kwin is so much better than compiz in my opinion.

---

