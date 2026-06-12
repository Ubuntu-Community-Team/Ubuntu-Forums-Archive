---
title: "Lost the bar at the top of ALL windows ??"
date: 2008-08-05
forum: Desktop Environments
---

### Post by teishu on 2008-08-05
Hi,

For some reason i booted my machine today and all the little bars at the top of all windows have disappeared. so i can't move, minimize, maximise or close as usual. See Screenshot.
Any help would be greatly appreciated...

---

### Post by perlluver on 2008-08-05
> **teishu said:**
> Hi,

For some reason i booted my machine today and all the little bars at the top of all windows have disappeared. so i can't move, minimize, maximise or close as usual. See Screenshot.
Any help would be greatly appreciated...

Press alt+f2 then type metacity --replace or emerald --replace if you are using compiz.  That should bring them back.

---

### Post by teishu on 2008-08-05
> **perlluver said:**
> Press alt+f2 then type metacity --replace or emerald --replace if you are using compiz.  That should bring them back.

Thats great !

Thanks mate....  :):KS

---

### Post by perlluver on 2008-08-05
> **teishu said:**
> Thats great !

Thanks mate....  :):KS

No Problem.

---

### Post by zagnut48219 on 2008-08-20
I'm a n00b to Ubuntu as well. Running Gutsy 7.1 + Compiz. I have the same problem. I open a terminal window, type emerald --replace and the bar reappears. But disappears as soon as I close the terminal window. How can I remedy this?

---

### Post by zagnut48219 on 2008-08-20
Disregard, I figured it out. 
emerald --replace & 
then ctrl+d

---

### Post by deejay427 on 2008-08-21
i did exactly as said and it didn't work what the heck am I doing wrong?

---

### Post by zagnut48219 on 2008-08-21
I'm running Gutsy and Emerald.

If typing in terminal - 
emerald --replace & (the symbol)
enter
then pressing ctr+d
doesn't work, try this.

Open the compizconfig settings manager. Either from System > Preferences > Advanced Desktop Settings or in terminal with ccsm
Goto Effects, make sure Windows Decoration is checked. Click on Windows Decoration to open it. You'll see a line "Command" option. Put emerald --replace in the box. 

Not sure if you'll have to restart compiz or not. To restart Compiz, terminal: compiz --replace

Oh, make sure that if you're using emerald, you have a theme imported and selected. System > Preferences > Emerald Theme Manager. My first attempt didn't work because I didn't have any themes. #-o D'OH!

---

### Post by jittopjose on 2008-08-22
my suggestion is put emerald --replace in start up programs. it will be automatically applied on startup..

---

