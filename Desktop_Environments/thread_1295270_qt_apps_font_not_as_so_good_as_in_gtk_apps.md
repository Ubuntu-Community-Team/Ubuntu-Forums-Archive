---
title: "qt apps font not as so good as in gtk apps"
date: 2009-10-19
forum: Desktop Environments
---

### Post by aim on 2009-10-19
I have a good (for me) fontconfig. All gtk apps look pretty cool, but I have problems with all qt apps (I use vlc, KeePassX).

Check out screenshot attached. 

The question - how to fix qt apps and make fonts look the same way as in gtk apps?

[IMG]http://img.aim.pp.ru/2009/10/19/Screenshot.png[/IMG]

---

### Post by anagor on 2009-10-19
Hi,
There is a package in repositories named qt4-qtconfig
after installation it will be located in 
"System->Prefences->Qt 4 Settings"
All the rest is quite self explanatory there, but don't forget to save the settings, (ctrl-s) or File->Save :)
You can make the Qt applications to use the same font as your gtk applications or any other font you wish.

---

### Post by aim on 2009-10-19
> **anagor said:**
> Hi,
There is a package in repositories named qt4-qtconfig
after installation it will be located in 
"System->Prefences->Qt 4 Settings"


there is no font configuration out there. other ideas?

---

### Post by anagor on 2009-10-19
Yes there is.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=132408&stc=1&d=1255969839[/IMG]

---

### Post by aim on 2009-10-19
> **anagor said:**
> Yes there is.


i mean there is no place like GNOME's system -> preference -> appearance -> fonts 

where one can configure antialias, hinting and other fontconfig options.

---

### Post by anagor on 2009-10-19
You are right.
But for some reason on my ubuntu the qt apps are all hinted and anti-aliased properly. hmm..

---

### Post by aim on 2009-10-19
Topic could be closed. 

What I did:

run qtconfig
changed style to GTK+
saved this and closed qtconfig

THEN opend gnome fonts settings and changed it once to anything then to the right options. 

and it worked - now qt apps have good fonts as gtk's apps previously did.

I know it sounds like a magic - but I currently have no idea what was THAT...

---

