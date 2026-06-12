---
title: "Root"
date: 2006-02-01
forum: Desktop Environments
---

### Post by PandabeaR on 2006-02-01
How can I log in as administrator or "root"? I need to do this so i can acess the files on the last 3 quake 4 cd's and install some other programs. Can anyone please help?

---

### Post by redmansk8 on 2006-02-01
from terminal type sudo and the command you want to do.
you will be asked for you password. sudo is like administrator.

$sudo ./install

---

### Post by PandabeaR on 2006-02-01
Thanks. Awesome avi btw. "Shop smart. Shop Esmart"

---

### Post by aysiu on 2006-02-01
[QUOTE=PandabeaR]How can I log in as administrator or "root"? I need to do this so i can acess the files on the last 3 quake 4 cd's and install some other programs.[/QUOTE] Actually, you don't *need* to log in as root. You can make your life a lot easier by doing Alt-F2 ```
gksudo nautilus
``` which gives you temporary root privileges within your user account.

---

### Post by PandabeaR on 2006-02-01
Ahh, thanks much :)

---

### Post by PandabeaR on 2006-02-01
also, I have a .run type fiile, it opens up in the typepad... its actually americas army. How do i get that to "run"?

---

### Post by Sutekh on 2006-02-01
```
chmod +x <nameoffile>.run
```
This makes the .run file executable
```
./<nameoffile>.run
```
will execute it.

or
```
sh <nameoffile>.run
```
should do the same, without chmod'ing it.

---

### Post by Patrick-Ruff on 2006-02-01
a very quick way of getting to Root terminal is by going to Applications, System Tools, Root Terminal.  it would also make it much faster by copying it to your desktop or top/bottom bars.

---

### Post by PandabeaR on 2006-02-02
Is there any way to GIVE my regular user access privilages to certain things? Cause I am finding it quite difficult to go into the quake4cd/quake4/data/q4base/ then selecting the files i want, archiving them, then extracting them from the root folder to the Home/Games/Quake4/q4base/ folder in my user. Its quite time consuming :(

---

