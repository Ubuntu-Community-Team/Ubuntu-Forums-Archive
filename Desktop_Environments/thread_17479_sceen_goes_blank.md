---
title: "sceen goes blank"
date: 2005-02-28
forum: Desktop Environments
---

### Post by sanman_nor on 2005-02-28
so I am runing a toshiba satilite, and sometimes, but not always, the screen will go blanke after being off for a while. but nothing I do will bring it back what should I do

---

### Post by doitashimashite on 2005-02-28
Next time this happens, try CTRL-ALT-BACKSPACE. This will restart the X-server.

Also try

Computer
Desktop Preferences
Screensaver
Blank after: put a higher value here, let's say 50 minutes
Advances: disable "power management" for a while. See if this helps.

---

### Post by sanman_nor on 2005-02-28
power mangagement is disabeled, and some times I would open the sceen saver box, and check and uncheck power management and it would not go blank, and other times it does not go blank
tried doing ctrl alt bksp nothing happened

---

### Post by sanman_nor on 2005-03-01
if I open the sceensaver diolog box  and just close it.  it  does not go blank

---

### Post by Jet2k5 on 2005-03-01
Sounds like you might have to start the xscreensaver deamon at startup.  I just a few days ago had my computer screen go black, and it locked up hard.  Nothing I did brought the screen back, I eventually had to hard-reboot it.

I'm still sort off the gnome & ubuntu newbie, but you might have to add it to some list/file where the xscreensaver daemon will be started on boot time.

Maybe one of you guys who is more experience might tell us?

---

### Post by sanman_nor on 2005-03-04
I have found the only way to make the comp turn on the screen is to press the power button.  and wait for it to shut down, then I can start it up  fine, but other then that nothing seems to work

---

### Post by sanman_nor on 2005-03-17
to deal with this I have started opening the screansaver in desktop preferances  and click on the advanced tab and click and unclick power enabeled, and this usaly works and the screen will not go black the screen saver will start up eventualy

---

### Post by ManiacMac on 2005-03-17
I have experienced this issue as well win an NC8000.  What I do when this happens is alternate between TTY1 and TTY7.  if you try to flip to one, wait a couple of seconds, then flip to the other, that normally will fix it within a few tries.  Its prolly a bit better than hard kill of the X Server (ala CTRL+ALT+BACKSPACE)

---

