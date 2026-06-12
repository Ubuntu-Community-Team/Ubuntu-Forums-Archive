---
title: "Can't get fonts installed"
date: 2005-06-25
forum: Desktop Environments
---

### Post by John Jason Jordan on 2005-06-25
I have 12 Truetype fonts I seriously need for classes in Linguistics (IPA fonts). These are Truetype fonts. I followed the instructions which said to put them in /usr/share/fonts/truetype in order to make them available to all users, and then they should appear. After doing so I opened a document in OO.o Writer, but they do not appear in the font list or in the insert special character font list.

The instructions said that if they did not appear, to enter the fc-cache command to refresh the font cache. This also failed to get them to appear.

Is there a Gnome GUI font installer utility? Or at least a simple foolproof way for someone to install a font and make it available to all users?

---

### Post by Petrush on 2005-06-26
Correct me if i'm wrong, im not an expert, but was messing about with this thing a few weeks ago.

You can install fonts by opening "fonts:///" in nautilus "browser", this will install them for your user. Drag'n drop the fonts there (i used opentype fonts, but from what i understood it should be the same). You can check if your fonts are available by opening, i.e. the font preference panels, and click the change font for some parts (don't change, just see if they're there).

Openoffice seems to be next issue. It seems to have it's own font system (please correct me if i'm wrong) and don't use same system as gnome. I have not managed  to get my opentype fonts to work in open-office.. unfortionately. I use OOo beta m104.

---

### Post by mcelroyj on 2005-06-26
[QUOTE=John Jason Jordan]I have 12 Truetype fonts I seriously need for classes in Linguistics (IPA fonts). These are Truetype fonts. I followed the instructions which said to put them in /usr/share/fonts/truetype in order to make them available to all users, and then they should appear. After doing so I opened a document in OO.o Writer, but they do not appear in the font list or in the insert special character font list.

The instructions said that if they did not appear, to enter the fc-cache command to refresh the font cache. This also failed to get them to appear.

Is there a Gnome GUI font installer utility? Or at least a simple foolproof way for someone to install a font and make it available to all users?[/QUOTE]
 You can also copy the fonts to the .fonts directory in your home directory.  That's why I've always done.

---

### Post by Xian on 2005-06-26
[QUOTE=mcelroyj]You can also copy the fonts to the .fonts directory in your home directory.  That's why I've always done.[/QUOTE]
That's true, but it will not make them available for all users which is what the member is attempting to accomplish.

---

### Post by Alexander Kirillov on 2005-06-26
[QUOTE=John Jason Jordan]I have 12 Truetype fonts I seriously need for classes in Linguistics (IPA fonts). These are Truetype fonts. I followed the instructions which said to put them in /usr/share/fonts/truetype in order to make them available to all users, and then they should appear. After doing so I opened a document in OO.o Writer, but they do not appear in the font list or in the insert special character font list.

The instructions said that if they did not appear, to enter the fc-cache command to refresh the font cache. This also failed to get them to appear.

Is there a Gnome GUI font installer utility? Or at least a simple foolproof way for someone to install a font and make it available to all users?[/QUOTE]
 Do they appear in font selection dialog in GNOME? E.g. in preferences->fonts?

---

