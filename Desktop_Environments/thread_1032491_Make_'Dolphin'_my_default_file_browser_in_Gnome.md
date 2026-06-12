---
title: "Make 'Dolphin' my default file browser in Gnome"
date: 2009-01-06
forum: Desktop Environments
---

### Post by optimistique1 on 2009-01-06
Hi All

I have Ubuntu 8.10 installed with both Gnome and KDE.

I was wondering how to make 'Dolphin' my default file browser in Gnome.

If this is possible, how?

The attached link shows how to change every other file manager except for Dolphin :-(

Many thanks

Garry

[http://psychocats.net/ubuntu/nonautilusplease](http://psychocats.net/ubuntu/nonautilusplease)

---

### Post by eatberrys on 2009-01-06
I assume you all ready have dolphin installed if not run sudo apt-get install Dolphin

then right click on any folder go to tab "open with" and dolphin should be listed there click it apply the setting and all your files should open in Dolphin now.

*edit* this worked when i clicked "home" but not when i clicked the folder on my desktop that i appled it to hope it works for u!

---

### Post by joaowojcikiewicz on 2010-04-04
*bump*

Try this:

Type this on terminal:
> gksu gedit /usr/share/applications/nautilus-folder-handler.desktop

Then edit the line "Exec=nautilus --no-desktop %U" to "Exec=dolphin %U", then save the file and it's done

---

### Post by Linux4Pedro on 2010-06-30
Thanks very much for your help. I love Dolphin and i rather not install kubuntu.

---

### Post by dudesurge on 2010-08-04
> **joaowojcikiewicz said:**
> *bump*

Try this:

Type this on terminal:


Then edit the line "Exec=nautilus --no-desktop %U" to "Exec=dolphin %U", then save the file and it's done

This didn't quite work for me, everything works except for specifically what i want,
Ok so it opens dolphin when i open a folder, and a removable drive "from places" but not when i open it straight from the desktop, that is what i want it to do, so you see my problem?
for anyone about to say, "then just don't open it from your desktop", Don't.
i'm not "new" to ubuntu but i am new in the sense that i don't know makefile or terminal to well, unless you give me very, VERY, specific instructions, 

if what i'm looking for is even possible please post a reply, if not don't bother

---

