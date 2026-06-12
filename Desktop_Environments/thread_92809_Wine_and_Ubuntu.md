---
title: "Wine and Ubuntu"
date: 2005-11-20
forum: Desktop Environments
---

### Post by bathini on 2005-11-20
Hello friends

I have just tried to install pplive on Breezy but complains that the folder can't be created. Initially when installing it defaulted to C:\program files\pplive and I decided to change to \home\pplive and it came up with the problem. I also tried with a different software sopcast prrogram and did the same thing. Please help and thanks.

Regards

bathini

---

### Post by Kevin on 2005-11-20
In wine /home means nothing to the program you are trying to install. You can install a program to your home directory by using x:\\pplive, where x is whatever drive wine assigned to your home directory.  You can find out what that is by running winecfg and looking at the drives tab.

I would suggest just using the default Program Files directory though.  This will install it to ~/.wine/c/Program Files/etc...

Kevin

---

### Post by Ampersand on 2005-11-20
I think you need to use a Windows like directory with Wine, so it'll have to start with C:\

---

### Post by aysiu on 2005-11-20
I install all my wine programs to ~/.wine/c_drive/Program Files/

---

### Post by bathini on 2005-11-21
Thanks for the answers but initially I started with C:\program files\ and that is when it did not work and that is why I change to linux directory of labelling. I think its something to do with the permissions somewhere?

bathini

---

### Post by Paul Chang on 2006-01-10
You don't need "wine" to install "sopcast". There is a debian package there. I installed on breezy, no any problems.

---

### Post by bathini on 2006-01-27
Where do I get this sopcast for debian??I can't find it on the repository. Thanks

Bathini

---

