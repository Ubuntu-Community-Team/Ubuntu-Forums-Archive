---
title: "I'm a tired newbie..,wiped basic menus&quot;apps,places, system&quot;off panel, help find them"
date: 2009-02-12
forum: General Help
---

### Post by mejbr2003 on 2009-02-12
I've been ubuntu-ing for a few weeks...
just wiped my Wubi away cuz I got my disc in the mail...
nice clean install
(if you hadn't heard, I "PARTITION"...a Partition-eerist?? , ...I partition..!! JoY)
on top of the world ma...then,
I need a nap, I've no idea what I did, clicked, moved, toggled...
but the nice words " Applications, Places, System", who's drop down menus are the only road map I can read in this strange land.
I don't even know what they are specifically called, to search for them...cant find any nice,
"restore panel items to original pristine default" button
help
I almost want my mommie, but she doesn't know what linux is
coming down from the "successful partition High!":confused:

---

### Post by loell on 2009-02-12
press

**Ctrl+Shift+T** for the terminal to appear


then type / or copy paste

```
gconftool-2 --load /etc/gconf/schemas/panel-default-setup.entries
```


see if it restores the menus and panels.

---

### Post by LowSky on 2009-02-12
If you still have a panel, just right click in the blank spot you want the menu, go to add application or whatever it says (Im on windows at the moment and the jargon isn't with me today)
....anyway, down the list you will see something withthe name _menu _(atually two version one will just be the Ubuntu Icon, the other will be the Icon plus all those words you miss

---

### Post by mejbr2003 on 2009-02-12
problem fixed, you all rock

---

