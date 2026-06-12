---
title: "password protect an application?"
date: 2008-12-10
forum: General Help
---

### Post by BrownieMan on 2008-12-10
Is it possible to password protect a specific program without doing anything too complex? I'd settle for only root being able to access the program. This program is pretty much all GUI fyi.

---

### Post by gettinoriginal on 2008-12-10
Anyone who can access your computer with the main password can also access any "locked" files with the sudo command.  If you are the "owner" of the computer, then change the logon password and then either set up user accounts or let others use a guest account.

---

### Post by BrownieMan on 2008-12-11
> **gettinoriginal said:**
> Anyone who can access your computer with the main password can also access any "locked" files with the sudo command.  If you are the "owner" of the computer, then change the logon password and then either set up user accounts or let others use a guest account.

That is one option. But I'd much prefer to have one main account and just password protect sensitive information instead of any time I want to access those sensitive programs I have to switch to another account.

---

### Post by HermanAB on 2008-12-11
Make the program executable by root only, then configure the user in /etc/sudoers.  Read the sudoers file.  It is really self explanatory.  You can then launch it with a launcher on the desktop or in a menu that calls "gksudo /path/programname".

Cheers,

Herman

---

### Post by MG&amp;TL on 2011-09-13
EDIT: arrghh. cross posting, sorry.

---

### Post by sisco311 on 2011-09-13
Closed for necromancing.

---

