---
title: "more logged users"
date: 2015-02-09
forum: Desktop Environments
---

### Post by Skaperen on 2015-02-09
the drop down menu from the gear icon in the far upper right has 13 or  14 slots listing users i have recently logged in as on the desktop.  how  can i re-confirure this for MORE users?  say maybe 20 users or more.

---

### Post by sudodus on 2015-02-09
I don't know, but maybe you can anticipate more users than you can see in the screen. In that case maybe a ***terminal window command*** might be a good idea. If you want it fancy you could enter its result into a GUI application for example ***zenity***.

There may be a more efficient command line, but this one works for me

```
 users|tr ' ' '\n'|sort|uniq
```

and this one if you want the verbose user names

```
 for i in $(users|tr ' ' '\n'|sort|uniq);do grep "$i" /etc/passwd|cut -d: -f5|sed s/,*$//g ;done
```

or with zenity

```
 users|tr ' ' '\n'|sort|uniq|zenity --text-info --text=/dev/stdin
```

---

### Post by Skaperen on 2015-02-12
i use firefox under each user.

the menu is used to quickly switch to another user.

i use multiple users to isolate cookies and other files.

---

### Post by sudodus on 2015-02-12
I see. Let us hope someone who knows will chip in and help you.

---

