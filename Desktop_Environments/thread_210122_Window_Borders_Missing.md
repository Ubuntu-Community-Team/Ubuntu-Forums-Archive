---
title: "Window Borders Missing"
date: 2006-07-06
forum: Desktop Environments
---

### Post by TomAnthony on 2006-07-06
I was trying to install the XGL and Compiz effects, which didn't work, and now when I boot into gnome I have no window borders or title bar, and the window won't show up in the task bar. Any ideas on how to get these things back?

---

### Post by Epskampie on 2006-07-06
This is what worked for me:
Install gset-compiz
```

sudo apt-get install gset-compiz
```
run gset-compiz
make sure all the plugins on the left are enabled

complete reboot
(don't just restart X)

Hope that helps, can't promise anything. :)


* if it can't find gset-compiz you probably need to add the following repositories to your /etc/apt/sources.list:
```
deb http://www.beerorkid.com/compiz/ dapper main
deb http://xgl.compiz.info/ dapper main
deb-src http://xgl.compiz.info/ dapper main

```

---

### Post by llamakc on 2006-07-06
[quote=TomAnthony]I was trying to install the XGL and Compiz effects, which didn't work, and now when I boot into gnome I have no window borders or title bar, and the window won't show up in the task bar. Any ideas on how to get these things back?[/quote]

If you want the old Metacity borders back, open a terminal and type:

metacity --replace

That should fix you up until you have another go at Xgl.

---

### Post by TomAnthony on 2006-07-06
[QUOTE=llamakc]If you want the old Metacity borders back, open a terminal and type:

metacity --replace

That should fix you up until you have another go at Xgl.[/QUOTE]


Perfect, thnx, that worked.

---

