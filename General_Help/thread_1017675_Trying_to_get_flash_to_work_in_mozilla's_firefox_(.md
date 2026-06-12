---
title: "Trying to get flash to work in mozilla's firefox (not ubuntu's) on 64bit."
date: 2008-12-21
forum: General Help
---

### Post by Athanasius on 2008-12-21
I am running 8.10 64bit and after following [ubuntu community documentation - FirefoxNewVersion]("https://help.ubuntu.com/community/FirefoxNewVersion") and flash is not working.  I am getting the following from the terminal:
```
LoadPlugin: failed to initialize shared library /var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so [/var/lib/flashplugin-nonfree/npwrapper.libflashplayer.so: wrong ELF class: ELFCLASS64]

```
Is there something else I need to link besides /usr/lib/firefox/plugins?

---

### Post by fooman on 2008-12-21
i am using the flash 10 64bit for linux from here:

[http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

i am using ubuntu's firefox.  all i had to do was extract the tar.gz file, then copy the just extracted libflashplayer.so to my /home/<user name>/.mozilla/plugins directory....not sure how different it would be using mozila's version of firefox.

i did have to uninstall any flash stuff i had previously installed before installing this version.

works great for me.

---

### Post by Athanasius on 2008-12-22
Thank you it works.  I had to add a "plugins" folder.. I didn't catch on to that at first.

---

