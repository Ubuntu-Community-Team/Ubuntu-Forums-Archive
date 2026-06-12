---
title: "Unity desktop hide installed program"
date: 2012-07-02
forum: Desktop Environments
---

### Post by gp1247 on 2012-07-02
I am running a program that I would like to hide. It is installed under WINE and shows up in my "installed programs" section of dash home aka main menu. How do I hide this program? I would not like it on any menu.:confused:

---

### Post by mc4man on 2012-07-02
If it's showing in the Dash then there is a .desktop file (launcher) for that program. 
Where it is you'd have to find, may just be on the Desktop

If you open the .desktop in a text editor (open a gedit window & drop the .desktop (launcher) in to
Then add this line - 
```
NoDisplay=true
```

---

### Post by prismctg on 2012-07-02
Try Main Menu program .... its already installed by default

---

### Post by gp1247 on 2012-07-02
> **mc4man said:**
> If it's showing in the Dash then there is a .desktop file (launcher) for that program. 
Where it is you'd have to find, may just be on the Desktop

If you open the .desktop in a text editor (open a gedit window & drop the .desktop (launcher) in to
Then add this line - 
```
NoDisplay=true
```

No luck. It installed under wine so it is in C:\program (x86) etc etc. I looked but that file does not exist.

---

### Post by gp1247 on 2012-07-02
> **prismctg said:**
> Try Main Menu program .... its already installed by default

BY that you mean alacarte? I tried but it does not show up as it is installed via wine.

---

### Post by gp1247 on 2012-07-02
> **mc4man said:**
> If it's showing in the Dash then there is a .desktop file (launcher) for that program. 
Where it is you'd have to find, may just be on the Desktop
 
If you open the .desktop in a text editor (open a gedit window & drop the .desktop (launcher) in to
Then add this line - 
```
NoDisplay=true
```
 
 
I lied! You were dead on. It was just under ~.local/shared/applications
 
 
Thank you very much!

---

