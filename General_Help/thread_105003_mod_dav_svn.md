---
title: "mod_dav_svn?"
date: 2005-12-17
forum: General Help
---

### Post by Deemo on 2005-12-17
Hello.
I have recently installed subversion through apt, and the server itself runs fine. However, now I am trying to get it set up to tunnel through apache with mod_dav_svn. Unfortunately, not only can I not find the file anywhere over the internet, but its not included in the apt installation AND when i compiled the source code myself, i could not find the file.

Im really lost as to what to do next, and help would be greatly appreciated

---

### Post by ranf on 2005-12-17
I did a simple search for "ubuntu mod_dav_svn" on Google
and found this:
[http://www.blendedtechnologies.com/setting-up-subversion-on-ubuntu/11](http://www.blendedtechnologies.com/setting-up-subversion-on-ubuntu/11)

Maybe that helps.

---

### Post by Deemo on 2005-12-17
i have no problem installing subversion, i just dont know where the mod_dav_svn.so file itself. How can apache find a file that doesnt exist! the link you gave me explains how to install SVN, not where to get the apache module itself

---

### Post by ranf on 2005-12-17
Ok. Searched some more:
[http://packages.ubuntu.com/breezy/net/libapache2-svn](http://packages.ubuntu.com/breezy/net/libapache2-svn)

You need the universe repository enabled.

---

### Post by Deemo on 2005-12-17
ah that worked well thanks!

---

