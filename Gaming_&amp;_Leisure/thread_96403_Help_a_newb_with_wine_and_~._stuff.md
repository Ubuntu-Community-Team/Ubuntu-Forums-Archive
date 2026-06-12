---
title: "Help a newb with wine and ~/. stuff"
date: 2005-11-28
forum: Gaming &amp; Leisure
---

### Post by s monty on 2005-11-28
I just switch to ubuntu 5.10 from windows XP. I know my way around computers fairly well, I built mine, I can program (simples stuff like pong), etc. Well I installed wine using Synaptic. I just can't find the shortcut to run Wine. And also what does ~/. mean? I can't navigate to that :???: [http://img126.imageshack.us/my.php?image=screenshot8mm.jpg](http://img126.imageshack.us/my.php?image=screenshot8mm.jpg) is what I see when I go to filesystem in the file browser, file system, desktop, home, is all I see in the file browser. What am I missing? 

-by the way, gj with ubuntu guys. And any input appreciated, thanks!

---

### Post by SavageBeginner on 2005-11-28
For wine you need to run:
```
winecfg
```

After that you can run a windows program by typing in terminal
```
wine winprogramname.exe
```

or double click on the windows program in the file browser.

You can find wine in /usr/bin this is where most executable files are.

Keep in mind that wine is still very buggy and may not work correctly

---

### Post by stoffe on 2005-11-28
~ is a shortcut for your users home directory. To find the wine directory, which I assume is what you wanted to do, you can navigate to Home in the file browser, turn on showing of hidden files (CTRL-H) and find the directory .wine (~/.wine in a terminal). For some purposes, running the command winefile might help, it's a very crude file explorer inside the win emulation.

I really recommend you get the wine packages from winehq.org too, in some cases it's a world of difference from the ones in Ubuntus repositories at the moment. There's instructions for Ubuntu on the site (basically, add "http://wine.sourceforge.net/apt breezy/" as a repository).

---

### Post by s monty on 2005-11-28
[QUOTE=stoffe]~ is a shortcut for your users home directory. To find the wine directory, which I assume is what you wanted to do, you can navigate to Home in the file browser, turn on showing of hidden files (CTRL-H) and find the directory .wine (~/.wine in a terminal). For some purposes, running the command winefile might help, it's a very crude file explorer inside the win emulation.

I really recommend you get the wine packages from winehq.org too, in some cases it's a world of difference from the ones in Ubuntus repositories at the moment. There's instructions for Ubuntu on the site (basically, add "http://wine.sourceforge.net/apt breezy/" as a repository).[/QUOTE]
WOW that CTRL+H thing helped so much, I was wondering why the home thing was there, I saw nothing but desktop. Thanks a lot, you get the cool face 8-)

---

