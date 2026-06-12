---
title: "cedega"
date: 2006-06-06
forum: Gaming &amp; Leisure
---

### Post by pumbagris on 2006-06-06
Tried to install bf2 but it says i must be logged in as administrator to do this??
How do i do this??

Im new to ubuntu so all help is welcome

---

### Post by Flyn on 2006-06-06
Try sudo or gksudo before the command.

---

### Post by handy on 2006-06-06
[QUOTE=pumbagris]Tried to install bf2 but it says i must be logged in as administrator to do this??
How do i do this??

Im new to ubuntu so all help is welcome[/QUOTE]

I know little, but try typing **sudo** before the command, it may do it for you?

I can highly recommend the online help that is installed with Ubuntu as well.  It's not like the frustrating rubbish that windoze calls help! :grin:

***Menu:* System/Help** & make a choice?

**[EDIT:]  Hmm, great minds think a like...**

---

### Post by eqisow on 2006-06-06
You shouldn't need to be root (administrator) to install BF2, and you really don't want to be playing an online game as root.... how did you go about installing Cedega?

Note: Is it the BF2 installer giving the error, or Cedega?

---

### Post by siorai on 2006-06-06
Like eqisow said, you really shouldn't need to be root to install a game with Cedega. Did you actually install Cedega as root? That would more than likely explain the problem you're having.

---

### Post by frodon on 2006-06-06
I had this issue in the past and it was due to wrong rights on the .cedega directory in my home folder.
So i did a *chmod -R 777 $HOME/.cedega* and it solved the issue and i run all my games now as a simple user.

---

