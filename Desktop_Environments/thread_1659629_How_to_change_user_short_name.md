---
title: "How to change user short name?"
date: 2011-01-04
forum: Desktop Environments
---

### Post by marcogh79 on 2011-01-04
Hi everybody,

I installed Ubuntu 10.04 choosing, as administrator, a **[COLOR=Black]User Name[/COLOR]** and a **User Short Name**.
Now, I would like to change those names and I manage to do it with the first, but not with the second, the Short Name. At the same time, I would like to give the same new name to my personal folder in /home. Is it possible to do all that?

Thanks!!

---

### Post by Krytarik on 2011-01-04
IMO the only way to achieve this is to:

- create a new user, with the desired name
- copy the content of the home directory of the old to the new user
```
sudo cp -a /home/OLD_USER/* /home/NEW_USER/*
sudo chown NEW_USER.NEW_USER -R /home/NEW_USER
```
- log in with the new user and check if everthing is working
- if so, delete the old user

---

### Post by marcogh79 on 2011-01-19
Thanks for your answer.
I tried to create a new user and to do copy/paste of all my folders, but for the new user all the programs I installed are not there anymore... So I prefer not to delete the previous user.
Thank you, bye!

---

### Post by Krytarik on 2011-01-19
I suppose you mean programs under wine, they are in the .wine directory  in your home directory, I guess you can copy them over to the new user,  do "chown" and perhaps create some shortcuts. I don't know however, what  wine does when your user profile turns up under another linux user,  maybe you have to rename the profile dir or create a symlink to it with  the new name.

---

### Post by Krytarik on 2011-01-19
triple post due to forum error

---

### Post by Krytarik on 2011-01-19
triple post due to forum error

---

