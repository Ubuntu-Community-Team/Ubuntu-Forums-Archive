---
title: "[SOLVED] start a program w/o showing in task bar"
date: 2008-10-02
forum: Desktop Environments
---

### Post by oneadvent on 2008-10-02
I want to have my terminal application start without it showing in the bar at the bottom. (see attached picture) If I do that, it will be like its embedded into the desktop. 

Anyway, that would be cool to know anyway, any ideas.

---

### Post by oneadvent on 2008-10-02
Its cool, I figured it out and wanted to share:

I have compiz on, however, I found that if you only have it on when you start the program then turn it back off it still works well. I found that this was as close to "embedded" as it could get. 

I also chose to start the program (in Sessions) with the command:
```
xfce4-terminal --geometry 70x20
```
I am only using xfce4-terminal for this application so I changed all its values to show hidden title and I also changed the title itself to always be xfce4-terminal. That really made configuring this easy.

This command will error out and say it is wrong when you use this through a terminal but it works, so dont complain.

Let me know if you have any questions about this setup, I'll try to help.

---

