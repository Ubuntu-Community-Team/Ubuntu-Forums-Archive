---
title: "kde has no task bar or X windows"
date: 2006-08-10
forum: Desktop Environments
---

### Post by earobinson on 2006-08-10
When I run kde it comes up with the desktop and I can right click on that to open the run command dialog but I can not move the dialog or close it since it has no X or minimise or title bar.  any idea how I can get it running?

---

### Post by louis_nichols on 2006-08-10
is that so for all windows? I'd guess so...

Try opening the run dialog and entering the command *kwin* then <enter>. See if that helps.

---

### Post by earobinson on 2006-08-10
> **louis_nichols said:**
> is that so for all windows? I'd guess so...

Try opening the run dialog and entering the command *kwin* then <enter>. See if that helps.
That gets me the windows but still no kde taskbar

---

### Post by earobinson on 2006-08-10
> **earobinson said:**
> That gets me the windows but still no kde taskbar
Is there a way to force kde to reload itself?

---

### Post by earobinson on 2006-08-10
> 
Try running

```

kicker

```


When I run that I get an error saying that kicker cant talk to klauncher but when I try to run Klauncer it says it cant be started manually

edit: also things like firefox will run for a second then crash with an X windows error. I have no way to cut and paste ther error msg, using another computer to post this.

---

### Post by louis_nichols on 2006-08-10
> **earobinson said:**
> When I run that I get an error saying that kicker cant talk to klauncher but when I try to run Klauncer it says it cant be started manually

edit: also things like firefox will run for a second then crash with an X windows error. I have no way to cut and paste ther error msg, using another computer to post this.

hm... try issuing this command in terminal:

kdeinit

---

### Post by earobinson on 2006-08-10
> **louis_nichols said:**
> hm... try issuing this command in terminal:

kdeinit
It give an error saying that it looks like the dcopserver is all ready running.

Could type the whole error but that would take a long time since the computers are in different rooms :(

Edit: also Im using xterm, gnome-terminal seems to crash if I try and run it.

---

### Post by louis_nichols on 2006-08-10
> **earobinson said:**
> It give an error saying that it looks like the dcopserver is all ready running.

Could type the whole error but that would take a long time since the computers are in different rooms :(

Edit: also Im using xterm, gnome-terminal seems to crash if I try and run it.

well... strange problem you have... If all else fails and you're not extremely fond of your kde aspect, try logging out of kde and after that logging in a text terminal (with Ctrl+Alt+F1), then deleting the folder ~/.kde

then press Ctrl+Alt+F7 to go back to graphical installer and login as usual. You should go to  default, working, kde desktop.

---

### Post by earobinson on 2006-08-10
true, I will do that if i must but I would like to understand and fix the problem, maybe im just anal

---

