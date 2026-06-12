---
title: "Need help re-enableing unity"
date: 2011-11-24
forum: Desktop Environments
---

### Post by justtoplay on 2011-11-24
I was messing around with compiz trying to get my cube back and i accidentally disabled unity. I cant even find the terminal so i can try Unity --reset or something can i get some help?

---

### Post by ajgreeny on 2011-11-24
This should do it:-
```
gconftool-2 --recursive-unset /apps/compiz-1
unity --reset
```

---

### Post by justtoplay on 2011-11-24
Thank your for the code but knowing the commands was not the problem i cant seem to find the terminal :( .......

---

### Post by justtoplay on 2011-11-24
i might have a solution to not being able to find the terminal. What would be the file extension to run the code using a text editor threw the terminal? Like for the cmd its .bat what would it be for this terminal?

---

### Post by ajgreeny on 2011-11-25
Ctrl+Alt+T should get you a terminal, if not do it from Ctrl+Alt+F1 in the cli.  Login with username and password (pw will not show on screen as you type, but will be there) then run those commands.

---

