---
title: "Howto launch programs in desktop 2 from cmd line"
date: 2008-01-24
forum: Desktop Environments
---

### Post by kevinlam on 2008-01-24
Hi I have a habit of running specify programs on startup by a bash script but I would like to have X prog in desktop 1 and Y prog in desktop 2 so I can switch ard. 
any idea how to specify which desktop from the CMD line?

oh I am using gnome btw on 7.10

---

### Post by diaa on 2008-01-26
I think I have an idea for it, why not use some Window scripting software such as [wmctrl]("http://sweb.cz/tripie/utils/wmctrl/") to move the window to the desktop of your choice after you launch the application, for wmctrl this is possible using the -s parameter...

---

