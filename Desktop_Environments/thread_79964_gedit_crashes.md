---
title: "gedit crashes"
date: 2005-10-21
forum: Desktop Environments
---

### Post by hekata on 2005-10-21
Hi, I'm eperiencing that problem - when I try to open file as a root from the terminal with gedit, it crashes. It says it can't load the display. The same problem with the other text editors.
The thing is that when I start gedit from the Start Menu, it works. But to edit some files (like /etc/fstab) I need a root access.
Do u have any idea how to fix that?

---

### Post by Gandalf on 2005-10-21
[QUOTE=hekata]Hi, I'm eperiencing that problem - when I try to open file as a root from the terminal with gedit, it crashes. It says it can't load the display. The same problem with the other text editors.
The thing is that when I start gedit from the Start Menu, it works. But to edit some files (like /etc/fstab) I need a root access.
Do u have any idea how to fix that?[/QUOTE]
When do ppl understand that this ain't a board to ask questions :roll: :roll:

---

### Post by matw on 2005-10-29
Huh? I just read KingBahamut's sticky, and it sure seams like this is the right place. It's a "problem with desktop software".

> 
Who's This Forum For?

* Desktop Support....You see we have four essential groups in our society, Police, Ambulance, Fire, Desktop Support.

* You Have an intermediate to advanced problem with desktop software.

* You Have an application you would like to discuss at length.


Why not answer the question? Had you, I might have benefited.

If it's wrong to ask questions, then maybe KingBahamut can edit the sticky and say "People need to realize this board ain't to ask questions". People like me with questions about desktop software problems will then stay away.

Also, if this isn't the place, then where should one ask questions like hekata's?

---

### Post by matw on 2005-10-29
Hekata,

This isn't an answer to your question, but it might help. I was running into the same problem because I was running as root in a terminal ("su -") and couldn't edit anything with gedit.  On the other hand, I coulndn't gedit the files as myself because I didn't have permission, and "sudu gedit &" wouldn't let me enter a password.

The solution I found is

$ sudo -b gedit

This lets you continue on with your terminal session while editing your files with root permission.

Let me know if you solve the Gtk error problem.

---

### Post by matw on 2005-10-30
I've figured out what's going on with the Gtk error.

'su -' creates a root shell that lacks all of the environemnt variables that the GNOME desktop needs to run a gui app (like gedit).

'sudo -b gedit' provides those environment variables (ref. 'sudo printenv'), but doesn't provide you with a root shell.

'sudo -b gnome-terminal' provides a root shell with all the environment variables needed to run gui apps.

Hope this helps.

---

