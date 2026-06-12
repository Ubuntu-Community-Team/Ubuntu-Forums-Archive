---
title: "Can't open apps under root. X problem?"
date: 2005-04-17
forum: Desktop Environments
---

### Post by Sham on 2005-04-17
Hi all,

I can't seem to use gui applications when logged in as root. I can as a user though which is strange. If I type (as root):

>nedit sources.list

I get:

Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

NEdit: Can't open display

but:

>sudo nedit sources.list

will work!

Any ideas?

TIA

---

### Post by deadlands on 2005-04-17
[/QUOTE]
 I think others will be able to answer this better than I, but I think it's because only your user is allowed to connect to the X server. I fixed it by this command:
```
xhost +localhost:
```  <<--- note the colon at the end.

I guess this allows local users including root to connect to the X server.

---

### Post by Sham on 2005-04-17
[QUOTE=deadlands][/QUOTE]
 I think others will be able to answer this better than I, but I think it's because only your user is allowed to connect to the X server. I fixed it by this command:
```
xhost +localhost:
```  <<--- note the colon at the end.

I guess this allows local users including root to connect to the X server.[/QUOTE]

i assume I will have to do this everytime i reboot the box?

---

### Post by deadlands on 2005-04-17
[QUOTE=Sham]
i assume I will have to do this everytime i reboot the box?[/QUOTE]

Perhaps. Now I'm a bit miffed, I can't get it to work, yet it was working yesterday. I hope someone gets on here and helps clear this up.

---

### Post by windymiller on 2005-04-18
[QUOTE=deadlands]Perhaps. Now I'm a bit miffed, I can't get it to work, yet it was working yesterday. I hope someone gets on here and helps clear this up.[/QUOTE]
 I thought it was "xhost +local:" (not localhost)?  That's what I use anyway.  I've put that command on the end of my .bash_profile, so I don't need to keep entering it all the time.

---

### Post by Sham on 2005-04-18
[QUOTE=windymiller]I thought it was "xhost +local:" (not localhost)?  That's what I use anyway.  I've put that command on the end of my .bash_profile, so I don't need to keep entering it all the time.[/QUOTE]

How come we have to do this in the first place? It worked fine under Gnome.

---

### Post by Glanz on 2005-04-18
[QUOTE=Sham]How come we have to do this in the first place? It worked fine under Gnome.[/QUOTE]
As sudo, in GDM Setup under 'security', you can give root permission to login to the x server as root. I don't know about KDM though....

---

### Post by bugmenot on 2005-08-14
If you are using `su` to become root, you should instead use `sux`.

---

