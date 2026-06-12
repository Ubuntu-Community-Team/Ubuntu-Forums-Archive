---
title: "Apps wont stay in startup list"
date: 2005-10-27
forum: Desktop Environments
---

### Post by lost.sync on 2005-10-27
after using Automatix, my startup programs list is blank in Gnome's Sessions dialog.  adding any programs to it is fruitless, as it's blank the next time i open it.  it works fine with other user accounts, just not my own.  i have reinstalled gnome-session, gnome, and ubuntu-desktop in hopes that it'd fix it, but it hasn't.

any ideas?

edit: nevermind.  i got it.

just in case this happens to anyone else:

/home/username/.gnome2/

you are looking for: session-manual and session-manual_backup

in my case, session-manual was completely blank, so i just removed it.  

then, obviously, rename session-manual_backup to session-manual

and then you're good.

---

### Post by vassalle on 2005-10-27
i have the same problem too, however i dont have the session-manual_backup file, and the session-manual file is empty. what should i do ?

---

### Post by lost.sync on 2005-10-27
the syntax of the file is pretty simple...you should be able to create a new one from scratch and then you can use the GUI tool to add new items to it so that you don't have to do it manually.

so...

1. $ sudo gedit ~/.gnome2/session-manual
2. edit as described below
3. save and exit gedit
4. $ chmod 644 ~/.gnome2/session-manual

i think all you'd need in the file is...

```
[Default]
num_clients=0
```

to have a file that gnome-session-properties could read and add things to.

also, i don't know if it's really picky about it or not, but in my session-manual, the first line is blank.  

here is mine:
```
[Default]
num_clients=3
0,RestartStyleHint=3
0,Priority=10
0,RestartCommand=yakuake 
0,Program=yakuake
1,RestartStyleHint=3
1,Priority=50
1,RestartCommand=logjam 
1,Program=logjam
2,RestartStyleHint=3
2,Priority=50
2,RestartCommand=gaim 
2,Program=gaim
```

---

### Post by vassalle on 2005-10-27
thanks for the quick reply.. will try it soon! gotto go to bed now.. no time to fiddle around. ;)

---

### Post by Zymous on 2005-10-29
Same here. On my system session-manual and session-manual.bak were owned by root. Changing the owner to the session owner allowed Apps to stay in the startup list.

-- 
Zym

---

