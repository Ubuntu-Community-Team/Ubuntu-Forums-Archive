---
title: "trouble with java"
date: 2009-03-06
forum: General Help
---

### Post by phillip1882 on 2009-03-06
i'm able to download and install java fine, but i can't get firefox to associate with the downloaded file. every time i try, i get permission denied. here's what im doing. first get into the necessary file folder,
cd /usr/lib/firefox-3.0.7/pluglins
then run the link command,
ln -s /phillip/java/jre1.6.0_12/plugin/i386/ns7/libjavaplugin_oji.so
but this is what gives me permission denied. (the java file is in my home directory, but i cant seem to move the java file to the usr directory.)
any suggestions would be welcome.

---

### Post by taurus on 2009-03-06
You don't have write permissions outside of your $HOME so if you want to link something outside of your $HOME, include the sudo in front of the command.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by phillip1882 on 2009-03-06
all right yeah it appears my file system is locked. i cant create or move folders into it whatsoever. anyone know how to unlock it?

---

### Post by taurus on 2009-03-06
Which filesystem?  

Which directory (or directories)?

---

