---
title: "gftp - really weird problem"
date: 2007-04-08
forum: Desktop Environments
---

### Post by balaram on 2007-04-08
I've been using GFTP to network four Dapper 6.06 computers for several months. Suddenly a connection problem has arisen on just one of the computers.
  If I start GFTP via a desktop icon (application launcher) it won't connect to any computer but if I start the program from the root terminal it will connect to every other computer. 
  Oddly the options I set on the program that launches from the desktop don't match the options on the program launched from the terminal. Of course even when I change the settings it still won't connect. 
  I did a complete removal of GFTP but upon re-install the same exact thing happeneds (Oh woe is me...shades of Windows). 
 I could continue to start the program from terminal but it's just extra steps I can do without, and besides now I want to get it working right just for the sheer satisfaction of it.

---

### Post by balaram on 2007-04-08
Solution was simple, I added sudo to the command line in  Launcher Properties (sudo gftp %u) and now it connects. Odd thing was that command line on other computers doesn't require sudo and they work fine.
 Now if I could just get xinerama working again life would be beautiful.

---

