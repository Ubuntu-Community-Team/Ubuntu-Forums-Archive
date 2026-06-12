---
title: "Wine trouble?"
date: 2006-11-02
forum: Gaming &amp; Leisure
---

### Post by casperiv on 2006-11-02
I was following one of the "How to get WoW in Ubuntu" threads and had an interesting issue... when I tried to compile and install wine it did it, but when I try to configure wine it says there is a problem with "c:\program files\" and such.  It looks like wine can't find it's own files.  When I navigate to .wine and look, it has the correct folder structure.

Any ideas?  If I go to take this off and try again, where do I need to go to remove everything to try again?  Sorry I can't give you the exact error.... I'm working graveyard tonight and it has been bugging me since I left home.  I will post more details when I get off in the morning.

---

### Post by reiki on 2006-11-02
I'm not sure which directions you followed. If you compiled wine (downloaded the sources and did the whole ./configure, make depend, make, make install...) then you would go back into the directory where the sources are and from where you were compiling and issue the command sudo make uninstall

You'll see it removing the files it installed.

I have another post on here about wine, WoW and Edgy. It has instructions that don't involve you haveing to compile by hand (apt does everything for you) and it results in a .deb file that you can then install normally usaing dpkg -i the-name-of-the.deb. 

I now have WoW running in Edgy and it runs as well as it does in Dapper (with an older version of wine as I haven't upgraded that one yet)

---

