---
title: "Can't open files on desktop by double clicking them"
date: 2012-12-11
forum: Desktop Environments
---

### Post by ramakriok on 2012-12-11
Hello to everybody!

I'm using Xubuntu 12.04, XFCE 4.10, and Thunar 1.4.0.

Some weeks ago, i used this guide to replace Thunar with SpaceFM (changing wherever it said PCManFM for SpaceFM)
[http://blog.desdelinux.net/reemplazar-thunar-por-pcmanfm-en-xfce/](http://blog.desdelinux.net/reemplazar-thunar-por-pcmanfm-en-xfce/)

I've reverted it, uninstalled SpaceFM and everything went good. I installed LibreOffice as I need some options that Abiword and Gnumeric didn't give me. When clicking an ODT file, Abiword was opened, so I then uninstalled Abiword and Gnumeric.

When I try to open some .ODT, .XLS or .txt files on my desktop,  i get the error

"File can't be opened
Failed to execute program /usr/bin/Thunar: Success"

But when I open those same files from my desktop folder, using Thunar, I can open them normally. Also, I can open the trashcan from my desktop without any problem.

I can, for example, "right click>open with LibreOffice Writer", but I'd love to get the double clicking working again. How can I solve this problem?
Thanks in advance!
Ramiro

---

### Post by TheFu on 2012-12-11
Have you tried to reinstall LibreOffice so the extensions are reset in Thunar? Did that work?

$ sudo apt-get install --reinstall libreoffice-*

should be enough, but might install more things than you already have installed. It is probably best to use **Synaptic** with the reinstall option selected.

---

### Post by ramakriok on 2012-12-11
Thanks for your answer, but unfortunately I don't think that helps.

I can't copy+paste files to my desktop, or delete files in my desktop, but I can do that from my desktop folder using Thunar. I tried to play an .mp3 file, same results: "Failed to execute program /usr/bin/Thunar: Success" if I double click the icon on my desktop, opens in gmusicbrowser if I double click on my desktop folder in Thunar.

So the problem here isn't LibreOffice, but how Thunar works on the desktop.

---

### Post by TheFu on 2012-12-11
> **ramakriok said:**
> So the problem here isn't LibreOffice, but how Thunar works on the desktop.
Have you tried to reinstall Thunar?  Did that work?

Wish I could help more, but I don't use file managers.

---

### Post by ramakriok on 2012-12-11
Well, last answer "inspired" me.

I went to Synaptic, searched for Thunar and reinstalled it. 5 seconds later it was done and now it works as usual!

---

### Post by TheFu on 2012-12-11
> **ramakriok said:**
> Well, last answer "inspired" me.

I went to Synaptic, searched for Thunar and reinstalled it. 5 seconds later it was done and now it works as usual!

Great.  Sometimes settings get overwritten by other programs and the easiest way to put them back is with an app reinstall.

---

