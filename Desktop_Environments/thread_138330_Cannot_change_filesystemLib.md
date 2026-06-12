---
title: "Cannot change filesystem/Lib???"
date: 2006-03-01
forum: Desktop Environments
---

### Post by kirby_t07 on 2006-03-01
I am adminsitrator etc on my machine yet when trying to install some codecs i realized that i could not change any files on the file system as it said i was not the owner. Anyone else had this problem and could point me the right way?

On changing the permissions in file manager it will not allow me. ('you are not the owner so you cannot change these permissions'). :-k 

Thank you in advance ubuntu community on wihch i so heavily rely!

---

### Post by Ramses de Norre on 2006-03-01
You should use sudo to change files/directories owned by root.
You can do it from terminal with sudo in front of your commands or type sudo nautilus at terminal to open nautilus with root permissions.
Beware when doing this, you can destroy everything when operating as root!

---

