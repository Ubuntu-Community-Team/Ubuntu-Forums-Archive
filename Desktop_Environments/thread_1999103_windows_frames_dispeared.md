---
title: "windows frames dispeared"
date: 2012-06-07
forum: Desktop Environments
---

### Post by lalebarde on 2012-06-07
Hi all,

My wife account is strange : 
[LIST=1]windows frames have disapeared (so it is impossible to move windows)
The "Applications Button" widget in the xfce4-panel shows nothing thought it is here
[/LIST]

But on the other accounts, mine, childs ones, everything is alright.

First action I did to try to recover is to archive her home, suppress her account with full deletion, and recreate it. Then restore the archive except for the files and directories beginning with a dot at her root, like the ~/.config tree. It worked for a while then the problem appeared again. But I don't know the circonstances nor reasons. She only use a web browser and some multimedia applications.

Second action was to archive her ~/.config I have suspected, and replace it with the one of my account. Then I ```
chown -R ~/.config
``` to give her the ownership, and a ```
find ~/.config -exec sed -i -e "s/my_name/her_name/g" '{}' ';'
``` in particular because the config files contain paths to my account. The problem remains.

I really don't know where to look for and what. Any clue please ?

```
# cat /proc/version
Linux version 3.0.0-20-generic (buildd@batsu) (gcc version 4.6.1 (Ubuntu/Linaro 4.6.1-9ubuntu3) ) #34-Ubuntu SMP Tue May 1 17:24:39 UTC 2012

```

---

### Post by Toz on 2012-06-07
Sounds like the window manager (xfwm4) has crashed on her account. Restart it by Alt+F2 and running:
```
xfwm4 --replace
```

---

### Post by dzimney on 2012-11-30
I had a similar issue and went through my user config folders until I found the problem. Honestly I'm not exactly sure what caused the issue, but simply removing the ~/.cache directory fixed the problem for me.

Hope this saves someone some headache.

---

