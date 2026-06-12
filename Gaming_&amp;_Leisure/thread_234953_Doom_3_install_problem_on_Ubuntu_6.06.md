---
title: "Doom 3 install problem on Ubuntu 6.06"
date: 2006-08-12
forum: Gaming &amp; Leisure
---

### Post by willbeone_kenobi on 2006-08-12
Hi guys,i wonder if any of you could help me. I recently gothold of the new Ubuntu 6.06 (they sent me the LIVE cd instead if the normalcd/dvd) and installed it.

Then I tried installing DOOM 3 (with the file downloaded from [www.liflg.com](www.liflg.com)) but I got the following errormessage in the terminal:

"willbeone@willbeone-desktop:~/Desktop/Linux_software/Games/DOOM_3_+_ROE$ sudo sh doom3_1.3.1302-multilanguage.run
Password:
Verifying archive integrity... All good.
Uncompressing DOOM III1.3.1302-multilanguage Installer.........................................................................................
/home/willbeone/.setup6371: error while loading shared libraries: libgtk-1.2.so.0: cannot open shared object file: No such file or directory"

Now how do Iget this brilliant game running on my Ubuntu PC? It runs just fine on my OpenSuSE 10.1 box.

---

### Post by Perfect Storm on 2006-08-12
You are missing libgtk 1.2. You can get it through apt-get

```
sudo apt-get install libgtk1.2
```

or search synaptic package manager.

---

### Post by willbeone_kenobi on 2006-08-12
Thanks for the help, but there is one problem. My ubuntu machine does not have access to the internet, can someone please provide me with a URL to the file so that I can download it from my dads Windows Xp (uugh!) machine and transfer it to my Ubuntu pc.

---

### Post by Perfect Storm on 2006-08-12
[http://packages.ubuntu.com/dapper/libs/libgtk1.2](http://packages.ubuntu.com/dapper/libs/libgtk1.2)
Just make sure you have the dependency to it as well.

---

### Post by willbeone_kenobi on 2006-08-12
Thanks forthe url, Artificial Intelligence.

---

