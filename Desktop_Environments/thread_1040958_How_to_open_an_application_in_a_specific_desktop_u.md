---
title: "How to open an application in a specific desktop using terminal"
date: 2009-01-16
forum: Desktop Environments
---

### Post by mahan_h on 2009-01-16
Hi Everybody.
does any body know hoe to open a X application such as firefox, gedit and so on in a certain desktop using shell command in terminal?

Thanx alot.

---

### Post by cloudstrifejr1 on 2009-01-16
> **mahan_h said:**
> Hi Everybody.
does any body know hoe to open a X application such as firefox, gedit and so on in a certain desktop using shell command in terminal?

Thanx alot.

I'm fairly new to Ubuntu also. Is it something like this.
IN Terminal:

open /path/to/some.app

I could be totally off. If I find something else, I will post it :)

---

### Post by howefield on 2009-01-16
If you run compiz, you can use the Place Windows plugin to predetermine the workspace an application will launch on, thereafter whether you launch via the menu or terminal it will launch on your desired workspace.

(you would add a rule in the Fixed Window Placement tab > Windows with fixed viewport)

---

### Post by 3rdalbum on 2009-01-16
KDE4 and Kwin can do this too - open the program, right-click on its title-bar, go "Advanced > Special Application Settings". Under "Geometry", choose "Force" and whatever desktop you want the program to open on.

---

### Post by jure1873 on 2009-01-17
for xterm it's something like this
xterm -geometry +1200+1200

The desktops are aligned like a grid. So if your desktop is 1024x1024 that would put it onto the 4th. 
but I don't know if firefox has these geometry switches.

---

