---
title: "login problem"
date: 2006-02-01
forum: Desktop Environments
---

### Post by rlittler2001 on 2006-02-01
:confused: how to reset user password

---

### Post by earobinson on 2006-02-01
hope this helps [http://www.ubuntuforums.org/showthread.php?t=117400&highlight=live+cd+password](http://www.ubuntuforums.org/showthread.php?t=117400&highlight=live+cd+password)

---

### Post by rlittler2001 on 2006-02-01
[QUOTE=rlittler2001]:confused: how to reset user password[/QUOTE]
how can I reset username so I can login

---

### Post by earobinson on 2006-02-01
link dident help? maybe i dont understand your question, did you forgot your password?

---

### Post by rlittler2001 on 2006-02-01
[QUOTE=earobinson]link dident help? maybe i dont understand your question, did you forgot your password?[/QUOTE]
I manage to reset root password, but the username does not work

---

### Post by pito on 2006-02-01
If you did not forgot the password write command

passwd


/piotr

---

### Post by steve.horsley on 2006-02-01
You say you reset the root password. If so, you should be able to Alt-Ctl-F1 from the GUI login to get a console screen. Then login as root, then use the command **passwd pito** (or whatever your user name is). Alt-Ctl-F7 back to the GUI login screen and log in.

If you can't log in as root, boot from the install CD, at the boot prompt type **rescue** and press enter, then **passwd pito** at the command prompt, then reboot.

---

