---
title: "Permissions to read directory contents"
date: 2009-04-21
forum: General Help
---

### Post by texpat on 2009-04-21
In the file browser I navigate to, say, /root where I find a number of folders marked with an X. If I try to open them, I'm told I have no permission to do so. So I go to a terminal and type "sudo cd dirname" and (after typing the password) get "sudo: cd: command not found".

How do I access those directories?

texpat

---

### Post by powder on 2009-04-21
This doesn't work because the command "cd" is part of the shell, not an executable.  Use **sudo -i** to escalate your privileges and then run the command.  Use **exit** to return to user privileges.

---

### Post by dtoronto on 2009-04-21
```

gksudo nautilus
```
From the CLI should open up the directories in the GUI

---

