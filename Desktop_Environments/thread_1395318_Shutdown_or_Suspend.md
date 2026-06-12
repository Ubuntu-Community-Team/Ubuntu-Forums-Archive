---
title: "Shutdown or Suspend"
date: 2010-01-31
forum: Desktop Environments
---

### Post by WallaceTech on 2010-01-31
Guys.

using  irexec does anyone know the program i would run in order to put the machine in suspend or shutdown.

I can find the button on the remote i am just unsure of the program i need to run in the .lircrc file

Thanks in advance

---

### Post by efflandt on 2010-01-31
The **apropos** command is handy when you are not quite sure what a proper command is.  See **man apropos**, and try **apropos shutdown** and **apropos suspend**.

For example **sudo shutdown -h now** would shutdown and power down the system "now".  If you have other users, you might delay that to give them warning.

Although, I do not know what irexec is (I am guessing infrared remote control).

---

