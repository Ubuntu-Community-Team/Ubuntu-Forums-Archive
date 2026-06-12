---
title: "Gconf Database"
date: 2008-08-21
forum: Desktop Environments
---

### Post by ShareBuntu on 2008-08-21
Hi,

While using gconf-editor I've come across a few applications that I had purged still being present in my Gconf database. An example would be the application "drapes". I used "locate" to find any occurrence on my system after running "updatedb" - with no results. Yet, there is still an empty directory for it in gconf-editor.

Any idea how I can remove it? I'm rather meticulous about ruling my system with an Iron Fist.

---

### Post by Vivaldi Gloria on 2008-08-21
> **ShareBuntu said:**
> Hi,

While using gconf-editor I've come across a few applications that I had purged still being present in my Gconf database. An example would be the application "drapes". I used "locate" to find any occurrence on my system after running "updatedb" - with no results. Yet, there is still an empty directory for it in gconf-editor.

Any idea how I can remove it? I'm rather meticulous about ruling my system with an Iron Fist.

Check various config files in ~/.gconf.

---

### Post by puppywhacker on 2008-08-21
Hi,

the GConf XML files are spread over the system. Part is in the user's home and part (schema's) is in /etc/

~/.gnome2/drapes.xml

I don't fully understand the GConf2 other than that it works just as the windows registry, both a configuration blessing and a big mess.

An alternative to locate is find. I like locate better, but find has it's upsides as well

find ~ -name drapes*

---

