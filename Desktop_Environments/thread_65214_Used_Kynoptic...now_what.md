---
title: "Used Kynoptic...now what?"
date: 2005-09-13
forum: Desktop Environments
---

### Post by Leebert on 2005-09-13
Question: Once you use Kynoptic to install packages what are you supposed to do next. Do you still need to compile what's been dl'ed? The reason I ask is because I downloaded Ruby and mySQL stuff but Ruby isn't available from the shell and I don't see any mySQL stuff in the app menu.

Thanks for the help!

---

### Post by GeneralZod on 2005-09-13
What steps exactly did you take?  Kynaptic should handle the installation as well as the download.  

Oh, and just in case you overlooked this: it's "ruby", not "Ruby", so trying the latter from the command-line would fail :)

Also, you might want to use Synaptic (a GTK app) instead of Kynaptic, as it is far better :)

---

### Post by shakin on 2005-09-13
MySQL won't appear in the app menu because it's just a server. It should either already be running or will start after a reboot (or 'sudo /etc/init.d/mysql start' if you don't want to reboot).

If you install a MySQL GUI tool like mysql-admin it should appear in your apps menu.

---

### Post by Leebert on 2005-09-13
Thanks GeneralZod, I'll get synaptic and try it out. And yeah, I know it's 'ruby'. I just get a command not found error when I invoke it.

Thanks shakin. How do I go about looking at everything that is running in the background?

---

### Post by tonysathre on 2005-09-13
ctrl-escape will bring up a taskmanager like windows, and in a terminal typing ps -fu *username*  will show running processes, and typeing top in a terminal will also show running processes, there might be other commands that might be more of what your looking for, typing apropos process, or something to that effect might tell you some more commands that u can use to view process information.  

the apropos command is a very useful tool, it will tell u commands that can use to do a certain task or have the word that u put behind the apropos command in the simple help file

---

