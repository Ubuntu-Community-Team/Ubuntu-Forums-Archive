---
title: "Emerald Problem"
date: 2008-09-20
forum: Desktop Environments
---

### Post by danielgroves on 2008-09-20
I have been trying to install a theme using emerald.  When I click a theme I cannot see any way to apply it.  I found something online which said to type the following in terminal:
```

emerald --replace

```

After I did this the it was applied, but as soon as I rebooted it was back to normal.  

I'm not sure what I have done since it was at that stage, but now when I type emerald --replace in terminal I don't get any windows icons (close, minimize, restore).  

Any Suggestions? Thanks in advance for any help :)

---

### Post by benerivo on 2008-09-20
The emerald --replace command only lasts for the current session. To make this apply at every 'login/boot up' then make it a startup program (in gnome this is done with System>Prefs>Sessions and adding an entry which has the command emerald --replace).

It should be working for you every time you give this command, but it isn't. You must have all the relevant packages installed as it has worked before. Emerald needs compiz to be loaded before it will work, so make sure that compiz is working by trying compiz --replace then trying emerald --replace.

compiz --replce does not need to be entered as a startup program in Ubuntu as it can be set to begin as the default window manager in System>Prefs>Appearances.

---

