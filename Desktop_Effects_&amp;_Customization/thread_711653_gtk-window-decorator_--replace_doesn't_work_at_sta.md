---
title: "gtk-window-decorator --replace doesn't work at startup"
date: 2008-02-29
forum: Desktop Effects &amp; Customization
---

### Post by Redrazor39 on 2008-02-29
Every time I start up or log in my ubuntu partition, I have to go to [Alt]>[F2] then type ```
gtk-window-decorator --replace
``` all the time. I would like it so that it defaults to using the gtk window decorator instead of emerald. How can I fix this? I found a nice theme called water vapor for GTK 2 and it's just so subtle and balanced so nicely! Please help me default this at login.

Thanks

Right now, I'm on the last step of my sig (then I get :confused: again)

---

### Post by Sam Lars on 2008-02-29
Go to System > Preferences > Sessions and save your session with gtk decorator loaded (and check save session on logout).  If that doesn't work next time you come in, go back in there and try adding it in there...

---

### Post by Redrazor39 on 2008-03-02
That doesn't work :(

I also have CheckGmail and I was hoping it would work with that, too, but it doesn't :(

:confused::confused::confused:

Now what do I do? I want to make gtk-window-decorator default instead of the emerald one and I want to make it so checkGmail activates at startup

---

### Post by cookieofdoom on 2008-03-02
I don't know about gmail, but uninstalling emerald might help? Worst thing that can happen is you have no window decorations and have to reinstall it.

---

### Post by Redrazor39 on 2008-03-02
ya, but I was hoping I wouldn't have to because I might find another theme in emerald format that I really like to use and then I have to go through this whole process again...

---

### Post by mrmiserable on 2008-03-02
open ccsm - window decorations under command add  gtk-window-decorator --replace
now when compiz starts it uses this

or install fusion-icon and it lets you choose your window decoration

---

### Post by cookieofdoom on 2008-03-02
Well, it seems like Ubuntu is probably automatically starting up emerald. The only solution I can think of is to remove the emerald binary, or rename it so Ubuntu doesn't find it. I'd think the sudo apt-get install/remove emerald is a bit easier.

Maybe someone knows how to disable Ubuntu's strange desire to user emerald over gtk?

EDIT: Do what he said? ^^^

---

### Post by Redrazor39 on 2008-03-02
I tried the command in ccsm, but it didn't work.

TO cookieofdoom, I also wonder what setting puts emerald ahead in priority over gtk

---

### Post by mrmiserable on 2008-03-02
have you added emerald --replace in system/preferences/session by any chance

---

