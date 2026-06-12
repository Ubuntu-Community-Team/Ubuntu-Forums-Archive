---
title: "lost administrator mode"
date: 2005-07-09
forum: Desktop Environments
---

### Post by eMuNiX on 2005-07-09
Basically new to (K)Ubuntu, I had administrator mode working and used it to change my network card from auto-detect to a manually assigned address of 10.0.0.9 merely to tie up with the rules on my router.  Now that I have done this I can no longer logon in administrator mode.  Any thoughts on how I can get this back? ](*,)

---

### Post by eMuNiX on 2005-07-09
/slaps eMuNiX for not using the search function.

---

### Post by fig_jam_uk on 2005-07-09
[QUOTE=eMuNiX]Basically new to (K)Ubuntu, I had administrator mode working and used it to change my network card from auto-detect to a manually assigned address of 10.0.0.9 merely to tie up with the rules on my router.  Now that I have done this I can no longer logon in administrator mode.  Any thoughts on how I can get this back? ](*,)[/QUOTE]

Hi all you need to do is if your using KDE which it seems like you are, is open a console, then type

sudo kcontrol

then enter your administrator password

then you will have access to all sections of kcontrol as administrator...

hope this helps

---

### Post by eMuNiX on 2005-07-10
That didn't work, basically kept going in a loop of asking for the root password.  In the end cleared the user cache and reinstalled kcontrol and all is working again.

---

### Post by fig_jam_uk on 2005-07-10
oh weel nice one, at least you got it working again  :razz:

---

### Post by apokryphos on 2005-07-10
[QUOTE=eMuNiX]That didn't work, basically kept going in a loop of asking for the root password.  In the end cleared the user cache and reinstalled kcontrol and all is working again.[/QUOTE]
You might consider trying:
> kdesu kcontrol

---

