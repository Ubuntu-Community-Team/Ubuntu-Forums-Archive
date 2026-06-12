---
title: "Wine  0.9"
date: 2005-10-26
forum: Desktop Environments
---

### Post by rj686 on 2005-10-26
I just installed the wine 0.9 source from winehq.com. The ./tools/wineinstall and the make install part went fine but now when i went to run wine i get this. Can someone help me?


rj@LOFTNESS:~/wine-0.9$ wine
wine: error while loading shared libraries: libwine.so.1: cannot open shared object file: No such file or directory

---

### Post by rj686 on 2005-10-26
*bump*(sorry) im just really trying to get the new wine installed

---

### Post by rj686 on 2005-10-26
i noticed other people have had problems with it because of the messed up repo included in breezy, but i didnt get this from breezy i dl/ed the binary myself

---

### Post by rj686 on 2005-10-26
is wine 0.9 located in teh debian repository yet?

---

### Post by Leigh on 2005-10-26
Add these lines to your *sources.list*

deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

It worked for me without any errors.

---

### Post by rj686 on 2005-10-26
is the version you have 0.9 beta?

---

### Post by Cyril on 2005-10-26
In version 2005930 that error was accompanied by this message :

*************************************************
The installed Wine libraries will not be found!
You can either:
   Add the line '/usr/local/lib' to /etc/ld.so.conf and run /sbin/ldconfig
   export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib
*************************************************
*************************************************

I tried it and it worked for me.
Btw the way the file etc/ld.so.conf did not exists but I created it and added the line.

---

### Post by rj686 on 2005-10-26
thx dude now i got it running :)

---

