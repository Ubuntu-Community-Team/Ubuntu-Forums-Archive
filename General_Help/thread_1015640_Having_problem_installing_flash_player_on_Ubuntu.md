---
title: "Having problem installing flash player on Ubuntu"
date: 2008-12-19
forum: General Help
---

### Post by ragnarokeve on 2008-12-19
I am currently running Ubuntu 8.04 (hardy) and when i try and install the deb file from adobe i get an error message saying [Error: wrong architecture 'i386'] and i have no idea what to do.

---

### Post by rommyappus on 2008-12-19
Hello - Could you please indicate the file name of the .deb file and wither you installed the x86_64 version of ubuntu or just the x86 version?

Edit: you can find out wither you are using x86_64 or x86 by typing uname -a in a console.

---

### Post by ragnarokeve on 2008-12-19
i am running the x86_64 version and the file name is install_flash_player_10.deb it is the one for 8.04+

---

### Post by rommyappus on 2008-12-19
Ok, I believe you have a few choices.. you can install the x86 version in an x86_64 environment by installing the following packages
nspluginwrapper flashplugin-nonfree
If you want to get this working in firefox, this guide should work:
[http://ubuntuforums.org/showthread.php?t=439290](http://ubuntuforums.org/showthread.php?t=439290)

or you can get the experimental x64 version from adobe which (so far) has worked much, much better for me. (Previously, flash would either not show up or crash firefox) 

I'm having a bit of trouble finding it, but if I do I'll reply with it.

---

### Post by rommyappus on 2008-12-19
[http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html](http://labs.adobe.com/technologies/flashplayer10/releasenotes_64bit.html)

this has some install instructions as well.

---

