---
title: "How to change the default system shell? (permanently)"
date: 2006-08-13
forum: Desktop Environments
---

### Post by latebeat on 2006-08-13
Hi there, I want to change my shell from bash to the z shell. I can do export SHELL=/usr/bin/zsh but the setting doesn't stay? 
Is there a method to change it so that it will be the system-wide shell? That is in gnome-terminal, the root terminal, tty1 etc?  :-k   :-k 


thanks

---

### Post by kabus on 2006-08-13
You can set a user's default shell in /etc/passwd.
Just look for the line that contains your user name and change /bin/bash to whatever.
Make sure to enter the correct path to your preferred shell , or you won't be able to log in.

---

### Post by latebeat on 2006-08-13
Thank you that did it!!

---

### Post by taurus on 2006-08-13
Also a much easier way to do that is with the command

```

chsh

```

---

### Post by latebeat on 2006-08-13
Thanks a lot, very useful command!

---

