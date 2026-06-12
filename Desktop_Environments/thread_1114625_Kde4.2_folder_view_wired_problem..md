---
title: "Kde4.2 folder view wired problem."
date: 2009-04-03
forum: Desktop Environments
---

### Post by chanyunkwan on 2009-04-03
I installed the KDE4.2.1 desktop environment on Ubuntu and deleted the Gnome environment. Kde4.2 is really powerful.
By default, the folder view can show all your files in the desktop folder in a nice and transparent window. But somehow after I played with the applet on plasma and changed some settings. **the folder view changed in to a big icon**(surely, I can make it smaller), even I tried to change the setting for folder view, I can't get the original look back. 
Do anyone know how to fixed this?

thank you

**SOLUTION:**
I deleted the plasma configuration file in home folder. folder view backed to normal again.

/home/USERNAME/.kde/share/config/
just delete plasma-appletsrc & plasmarc in this directory.

---

### Post by inobe on 2009-04-03
i am sorry, not completely understanding what you mean by big icon ?

i have the same desktop but never had gnome, it's a fresh install of kubuntu.

---

### Post by chanyunkwan on 2009-04-03
> **inobe said:**
> i am sorry, not completely understanding what you mean by big icon ?

i have the same desktop but never had gnome, it's a fresh install of kubuntu.

like the screenshot here.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=108491&stc=1&d=1238738423[/IMG]

---

### Post by inobe on 2009-04-03
wow okay, never witnessed an folder icon that big 


click the folder view settings "little wrench" what are the current settings ?

also have you removed it and added a new folder view ?

you can do that from widgets selector

---

### Post by chanyunkwan on 2009-04-03
> **inobe said:**
> wow okay, never witnessed an folder icon that big 


click the folder view settings "little wrench" what are the current settings ?

also have you removed it and added a new folder view ?

you can do that from widgets selector


I tried to change each of the settings for it, but no luck.
I also tried to remove it and added a new one.  it doesn't work.

---

