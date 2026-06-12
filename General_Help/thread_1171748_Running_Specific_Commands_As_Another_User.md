---
title: "Running Specific Commands As Another User"
date: 2009-05-27
forum: General Help
---

### Post by rhololkeolke on 2009-05-27
I was trying to set it up so that I could have certain commands run as root without a password by certain users.  I read that I should edit the sudoers file but what I'm doing doesn't seem to be working.  I tried editing it with visudo to add ```
rhol ALL=(ALL) NOPASSWD:/usr/bin/update
``` However, when I run the command ```
sudo -u root -H /usr/bin/update
``` it lets me run every command and program as root without prompting for a password.  I just want that one command to run.  Can someone please explain what I'm doing wrong.  Thanks in advance.

---

### Post by prinny42 on 2009-05-27
I don't know much about /etc/sudoers myself, so I can't really explain how it works, but adding this to the end of it should enable you to run a specific command (and only that command) without a password:

```
yourusername ALL=NOPASSWD: /path/to/command
```

---

### Post by rhololkeolke on 2009-06-01
I added your syntax to my sudoers file and it still didn't work.  However, I decided I would check the owner of the script I had set as executable using ```
chmod u+x /path/to/script
```  It turns out that somehow either when I created the file or when I ran the command the owner had changed to root and so it wouldn't let me run it without a password.  I quick ```
chown rhol /path/to/script
``` changed the owner back to me and now it works exactly like I want it to.  Thanks for the help.

---

