---
title: "Changing passwords"
date: 2005-01-07
forum: Desktop Environments
---

### Post by jonny on 2005-01-07
Am I missing something really obvious?  I can't find a way for a user who's not a sudoer to change their own password through Gnome (ie no terminal sessions, please)

---

### Post by tiiim on 2005-01-07
[QUOTE=jonny]Am I missing something really obvious?  I can't find a way for a user who's not a sudoer to change their own password through Gnome (ie no terminal sessions, please)[/QUOTE]
 u tried computer -> system config. -> users and groups?

---

### Post by zeroK on 2005-01-07
[QUOTE=jonny]Am I missing something really obvious?  I can't find a way for a user who's not a sudoer to change their own password through Gnome (ie no terminal sessions, please)[/QUOTE]
 Or simply enter "passwd" in a terminal :-)

---

### Post by fng on 2005-01-07
tiim, you also need sudo to use that :(
Not using a terminal session is gonna be hard.

How about this? :
- Applications -> Run Application ...
- Fill in : passwd
- Click on Run.

---

### Post by tiiim on 2005-01-07
[QUOTE=fng]tiim, you also need sudo to use that :(
Not using a terminal session is gonna be hard.

How about this? :
- Applications -> Run Application ...
- Fill in : passwd
- Click on Run.[/QUOTE]
 if not 

passwd [username] in root console? i think it that way

but of cause thats in a console so you may not like that.

---

### Post by jonny on 2005-01-08
I'm not paranoid about terminal sessions, it' s just that they're not very user-friendly.  I guess that, as tiim suggests, I can create custom launchers for each user, but I was looking for something slicker.  Windows and KDE both have something suitable...

It's a family system used by a number of computer semi-literates aged 5-65.  I've been telling everyone that one big advantage Ubuntu has over Windows is its ease of use for computer noobs... guess I've just found a weak spot.

Fortunately, it's about the only one I've found  :-D

---

### Post by tiiim on 2005-01-08
[QUOTE=jonny]I'm not paranoid about terminal sessions, it' s just that they're not very user-friendly.  I guess that, as tiim suggests, I can create custom launchers for each user, but I was looking for something slicker.  Windows and KDE both have something suitable...

It's a family system used by a number of computer semi-literates aged 5-65.  I've been telling everyone that one big advantage Ubuntu has over Windows is its ease of use for computer noobs... guess I've just found a weak spot.

Fortunately, it's about the only one I've found  :-D[/QUOTE]
 i think its just for sucurity reasons you could just add other members to the sudo group but just means they could also damage your comp.

Alternatively as you said make a custom terminal script.

Im sure this be fix in GNOME in the future. Unless you make a new group which can edit that there still ways but yeah bit shame but secure i know KDE is very flexible in that area so unless you go extreme and download KDE from the universe?

---

