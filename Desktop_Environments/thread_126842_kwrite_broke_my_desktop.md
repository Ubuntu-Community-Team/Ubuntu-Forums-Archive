---
title: "kwrite broke my desktop"
date: 2006-02-07
forum: Desktop Environments
---

### Post by ashrack on 2006-02-07
I created a shortcut to ```
kdesu kwrite
```
But I get the following error and also the dekstop freezees.
```
KDEInit could not launch "Kdesu"
```
but if I run 
```
kdesu kwrite
``` in konsole all works great. 

Help would be greatly appreciated

ps. It's the same with KATE, but SYNAPTIC works great

---

### Post by claydoh on 2006-02-07
When you make the link to the application, just enter "kwrite" in the command box, then under "Advanced Options" check the "Run as Different User" box, leaving the username blank.  Then when you click on the icon, the password prompt will pop up.

btw.......how has this broken your desktop???????

---

### Post by ashrack on 2006-02-07
> When you make the link to the application, just enter "kwrite" in the command box, then under "Advanced Options" check the "Run as Different User" box, leaving the username blank. Then when you click on the icon, the password prompt will pop up.
I get the same error.

> btw.......how has this broken your desktop???????
It's not broken it just freezes the whole desktop.

---

### Post by claydoh on 2006-02-07
Does it happen still after restarting X (ctrl-alt-backspace)  in or rebooting? My searches for info have been fruitless.

---

### Post by ashrack on 2006-02-08
[QUOTE=claydoh]Does it happen still after restarting X (ctrl-alt-backspace)  in or rebooting? My searches for info have been fruitless.[/QUOTE]
yes it does :(

---

### Post by ashrack on 2006-02-09
come on, please don't tell me that this is not fixable? Since I've grown quite attached to KDE in the last week or so and don't wanna go back to GNOME with its little to none features compared to KDE

---

### Post by GeneralZod on 2006-02-09
[QUOTE=ashrack]
```
KDEInit could not launch "Kdesu"
```
[/QUOTE]

Does your shortcut say "Kdesu" or "kdesu" ?

---

### Post by ashrack on 2006-02-11
GENERALZOD
It 'kdesu' with a small 'k'

why?

---

### Post by ashrack on 2006-02-15
found a work arround. I have to set DCOP REGISTRATION to NONE.
Why is that so and do other ppl here get this error?

---

### Post by ashrack on 2006-02-16
so no one else have had this errors? I find it really strange since the same thing happens on 2 computers.
D following they have in common:
REISERFS, UBUNTU+KUBUNTU DEB installed afterwards, automatix, both running custom kernel with SWSUP2 support
So it is my believe that one of the things above is the fault for my errors. Since apperantly I am the only one getting them :confused

---

