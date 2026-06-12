---
title: "Softare installation in Ubuntu"
date: 2008-07-07
forum: Desktop Environments
---

### Post by arun.in on 2008-07-07
How can I access the softwares I installed in Ubuntu. A few number of softwares are automatically coming in the menu. I don't know how to access the majority of softwares and packages that are not added in the menu. Please help.

---

### Post by mcduck on 2008-07-07
That depends on what you have installed. Quite large part of software available in repositories are not actually graphical programs but instead different kinds of command-line applications and shared libraries (adding these to the menu would be rather pointless).

Usually  you can start a program froma  terminal simply using the program's name. For example running "firefox" will start Firefox. Youcan also find the correct executable for your program using the "which"-command. Runing "which firefox" will rspond "/usr/bin/firefox".

After you have confirmed the name of the program's executable you can justa dd it to the menu yourself. Right-click on the Applications-menu and select "Edit Menu".

---

