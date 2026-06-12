---
title: "Begginer help."
date: 2010-02-10
forum: Desktop Environments
---

### Post by Roll FizzleBeef on 2010-02-10
Okay, I'm running Xubuntu 9.10 on my <snip> Dell Inspiron.  I have thus far loved it and have had nearly no problems.  

However, I recently installed Starcraft using Wine, and doing so placed a .exe and .INK icon onto my desktop.  I do not want this icon on my desktop.  

So, my n00b question is, how do I move this icon off my desktop, preferably putting it in the "games" section under applications alongside ZSNES et al.  


Thanks in advance.  :p

---

### Post by Satoru-san on 2010-02-10
First of all watch your language.

Second, wine creates a folder in enlightenment, KDE, and gnome in the app menu. Your program should be there. I usually delete icons off of my desktop. I dont like anything that reminds me of windows.

If you dont have a wine folder then you can create one and then add a launcher for your program inside that folder make it execute this command.

```
wine /home/<YOUR USER>/.wine/drive_c/<GAME FOLDER>/game.exe
```

Give it a custom icon if you so choose.

---

### Post by Roll FizzleBeef on 2010-02-10
Thanks for the help, this got me where I wanted to be.  Sorry about the language, I *AM* from Jersey, so expletives tend to flow freely from me.  ^_^

---

