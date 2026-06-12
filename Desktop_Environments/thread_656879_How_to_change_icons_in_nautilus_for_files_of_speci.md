---
title: "How to change icons in nautilus for files of specific type?"
date: 2008-01-03
forum: Desktop Environments
---

### Post by chandru.in on 2008-01-03
Hi,

Though I moved away from Gnome due to its lack of configuration options long back, I found that Canonical polishes Ubuntu (Gnome) much more than Kubuntu (KDE).  So I installed Ubuntu Gutsy yesterday as a more polished distribution can be advocated to new users more easily.

I found that there is no visible way to change the icons for all files of a specific type.  I have quite a few Java desktop apps.  These .jar files are displayed by default with a plain white icon.  Is there any way to change these icons which can be suggested while converting someone to Ubuntu?

:confused:

---

### Post by spiff95 on 2008-01-03
> **chandru.in said:**
> Hi,


I found that there is no visible way to change the icons for all files of a specific type.  I have quite a few Java desktop apps.  These .jar files are displayed by default with a plain white icon.  Is there any way to change these icons which can be suggested while converting someone to Ubuntu?

:confused:

Open nautilus, navigate to the file whose icon you wish to change, right click on it and choose "properties" from the menu. Then left click on the icon to the left of the "Name" box and navigate to /usr/share/icons/hicolor/48x48/apps and choose an appropriate icon. Voila! The icon you chose is now associated with that type of file. :-)

---

### Post by chandru.in on 2008-01-03
@Spiff

Thanks for the effort.  Well, I had tried it.  But that changes the icon only for that particular file.  But I wanna change the icon for all files of that time in the whole filesystem.

Am I missing something?  I'm using Ubuntu Gutsy (7.10).

---

### Post by chandru.in on 2008-01-04
Has no one else tried this?

---

### Post by oomingmak on 2008-01-04
> **chandru.in said:**
> I found that there is no visible way to change the icons for all files of a specific type.  I have quite a few Java desktop apps.  These .jar files are displayed by default with a plain white icon.  Is there any way to change these icons which can be suggested while converting someone to Ubuntu?
You need to edit  /usr/share/mime/packages/freedesktop.org.xml and assign an icon for the .jar file type (but doing this is not for the faint-hearted).

A much easier option (using a pleasantly designed GUI) is to use the [AssoGiate]("http://www.kdau.com/projects/assogiate/") program. 

It's available in Add / Remove  programs (and Synaptic) and it's very straight-forward to use. You just find the file type from the list available (or make a new one if it's not listed) then click the change icon button to browse to an icon of your choosing.

---

### Post by chandru.in on 2008-01-04
That worked.

Thanks.  This forum rocks.

---

