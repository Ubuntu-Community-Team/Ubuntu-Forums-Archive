---
title: "Firestarter + GNOME"
date: 2005-11-23
forum: Desktop Environments
---

### Post by deadboy on 2005-11-23
OK this is my first post and im kinda of a noob, so go easy on me.  I'm running Ubuntu 5.10, with GNOME and Firestarter installed.  Basically i have firestarter setup to start on login, using ```
gksudo firestarter
```  it starts up and asks for my password in a little dialog box while GNOME is still firing up its enviroment. The problem is that its only up on the screen for about 3 seconds and then GNOME finishes its starting up and then the dialog goes missing.  This would be ok except that nothing functions on GNOME unless i first input the root pass for firestarter, but most the time the dialog is long gone by the time i get to my computer.  I end up having to do CTRL + ALT + Backspace to restart X.  Is there anyway that i can configure firestarter to use the same pass that i entered when i logged in? or is there a way for GNOME not to kill the dialog box.  A quick side note, does ubuntu automatically start ip tables on startup? and if so is it ok if firestarter doesn't run seeing as it is only a GUI frontend? i other words am i still protected by the ip tables firewall if firestarter doesn't run on startup.  My understanding is you only really need to use firestarter if you want to change iptables graphically?

Thanks in advance,
deadboy

---

### Post by Peter76 on 2005-11-23
hello, the answer for your problem is in the firestarter manual ( can be found at their website ).
Iptables is not started by Ubuntu, but it's part of the kernel. You can configure it using the iptables command, which is pretty difficult ( imo ). Firestarter handles this for you, but actually passes iptables commands to the kernel once it ( firestarter ) starts up

---

### Post by 23meg on 2005-11-23
You'll find answers to all your questions here:

[http://www.fs-security.com/docs/faq.php](http://www.fs-security.com/docs/faq.php)

---

