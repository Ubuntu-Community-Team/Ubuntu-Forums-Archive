---
title: "konqueror - view source document"
date: 2005-12-05
forum: Desktop Environments
---

### Post by bdr09166 on 2005-12-05
I can't believe I'm the only one with this annoying problem!! 
- Using konqueror to view any web page.
- View document source (CTRL+U)
- Kate complains, saying that the file was deleted.

Why is this happening? I've tried ubuntu, apt-get install kde, but still the same...

Please help me!

---

### Post by bdr09166 on 2005-12-06
[QUOTE=bdr09166]I can't believe I'm the only one with this annoying problem!! 
- Using konqueror to view any web page.
- View document source (CTRL+U)
- Kate complains, saying that the file was deleted.

Why is this happening? I've tried ubuntu, apt-get install kde, but still the same...

Please help me![/QUOTE]
For all the people with the same problem, I managed to work around like this:
- removed kate editor.
- downloaded the kate editor from the debian unstable repos.
- removed all the dependencies from the downloaded packages.
- made a dpkg -i katexxxx..deb

How come the kate from kubuntu behaves like this?...

---

