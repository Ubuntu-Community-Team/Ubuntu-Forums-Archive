---
title: "Transset-df"
date: 2008-03-31
forum: Desktop Environments
---

### Post by canistra on 2008-03-31
I am using openbox with xcompmgr, and would like to set transset-df to startup with transparency for trayer and conky, the transset-df -n "trayer" option does not work

---

### Post by urukrama on 2008-03-31
For trayer you can use its own transparence option. Run trayer with the following command (plus with whatever other options you want to use, of course):

> trayer  --transparent true  --alpha <value>  --tint <color>

See the man pages ("man trayer" in a terminal) for more info on how to use these. This will not give you true transparency, though, but I suppose that is not very important for something small like a system tray.

---

### Post by canistra on 2008-04-01
> **urukrama said:**
> For trayer you can use its own transparence option. Run trayer with the following command (plus with whatever other options you want to use, of course):



See the man pages ("man trayer" in a terminal) for more info on how to use these. This will not give you true transparency, though, but I suppose that is not very important for something small like a system tray.

man, I allready using this options... You didnt't understood what I want ...

---

### Post by urukrama on 2008-04-01
Then what do you want? :confused:

---

### Post by canistra on 2008-04-01
just to start transset-df with the stupid transparency for trayer on startup, how hard it's that to understand ?

---

