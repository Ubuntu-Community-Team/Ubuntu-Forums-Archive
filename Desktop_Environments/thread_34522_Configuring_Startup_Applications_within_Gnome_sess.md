---
title: "Configuring Startup Applications within Gnome sessions"
date: 2005-05-15
forum: Desktop Environments
---

### Post by VosaxAlo on 2005-05-15
[SIZE=2] ](*,)  ](*,) 
[FONT=Verdana]Hi to all,

I have a problem when I try to configure some applications startup in my gnome session.
For testing the problem I have added 3 applications in the session setting to startup, but only one of them really start.
The first attachment to this thread is a picture of the 3 application I have added.
Only the **"gedit"** program run when I start my gnome session. 
The other two programs, **"hexedit"** and **"firestarter",** don't really run but are displayed in the list of the current running programs with the "watch" symbol. The second attachment to this thread is a picture of the current running program list with the two "strange" entries.

Can you say me why these two applications don't start correctly?

thank you.
[/FONT][/SIZE]

---

### Post by tread on 2005-05-15
Is hexedit a console program or a xwindows program? If its a console program you would need to put in "xterm -e hexedit".

Maybe someone else can help out with firestarter .. but i suspect its the same thing .. the program is running in the background.

---

### Post by VosaxAlo on 2005-05-15
Yes, in effect hexeditor is a console program, and your suggestion is right. Now the program start correctly. Many thank's.

 O:)  O:)

---

