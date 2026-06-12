---
title: "Programs not showing file menu"
date: 2009-03-08
forum: General Help
---

### Post by kcredden on 2009-03-08
Folks: I've been noticing something odd lately, Gwenview, and several other programs have lost the menu bar 

This screen shot of the newest Gwenview:  [http://gwenview.sourceforge.net/screenshots.php?action=view&album=/1.4&pos=0](http://gwenview.sourceforge.net/screenshots.php?action=view&album=/1.4&pos=0)

shows Gwenview as it normally installed: On the menu section that reads 'file edit view...' That isn't showing up on Gwenview, and several *other* programs. I've tried to delete Gwenview's preferences but apparently I was only able to find some of them. 

So I'm asking; Does Gwenview use a type of universal menu display, and if so how do you edit, or at least reset it back to normal? De-install, and reinstall doesn't work. 

- Kc

---

### Post by Neo_The_User on 2009-03-08
Well you could try deleting the config files for Gwenview or whatever by hand. That will set it to default.

---

### Post by kcredden on 2009-03-09
Well, I deinstalled Gwenview, then used Krusader to search though my entire system, and I deleted all files marked 'gwenview'. But still it's only partly back to normal. The file menu as I mentioned before is still not showing up. Is there other files I'm missing? 

> **Neo_The_User said:**
> Well you could try deleting the config files for Gwenview or whatever by hand. That will set it to default.

---

### Post by kcredden on 2009-03-15
I finally solved this: 

I don't know what the command line version is, but if you use KDE 3.5 in Ubuntu 8.04.01, on the desktop, right click it, and it pulls up a menu that starts with: 

Create New, Run command...


Go down to: Configure Desktop, pulls up the menu marked: 

configure - Kdesktop

In 'Behavior'

If you have 'current application's menu bar (Mac OS-Style) marked, this is the source of this. Instead select 'Desktop menu bar' for a standard bar. 

I'm not sure exactly what is going on here, but it affects KATE, Kopete, and Gwenview as far as I know. 

Hopefully this will stop someone's headaches, I found ths answer totally by accident this morning.

- Kc

---

