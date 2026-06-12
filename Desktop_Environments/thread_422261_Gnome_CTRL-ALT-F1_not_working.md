---
title: "Gnome CTRL-ALT-F1 not working"
date: 2007-04-25
forum: Desktop Environments
---

### Post by hormati on 2007-04-25
Hello,
I am using Feisty. In my Gnome, CTRL+ALT+F1 does not work properly. When I press CTRL+ALT+F1, it takes me back to the console but there is no prompt. In the console window there is some text from the boot time. At that point, I can use CTRL-ALT-F7 to go back to Gnome again. Additionally, If I use  "sudo /etc/init.d/gdm restart" to do restart my gnome, gnome crashes and I have to reboot using CTRL-ALT-DEL. One more thing, before feisty I had edgy and CTRL-ALT-F1 was working in edgy. 
Does anybody have any solution?
Amir

---

### Post by RedSquirrel on 2007-04-25
You might have more serious issues going on, but try:

When you do Ctrl-Alt-F1 and get to the console (tty1), press ENTER. That should give you a prompt. 

Personally, I prefer to use Ctrl-Alt-F2 to go to a console  (tty2) that looks a little cleaner (i.e., there's nothing there but a prompt).

---

### Post by hormati on 2007-04-25
Thanks for the reply, but my problem is not that :). The console is not working. Any other ideas?
BTW, CTRL-ALT-F2 is also not working. It just brings up a black screen.

Amir

---

