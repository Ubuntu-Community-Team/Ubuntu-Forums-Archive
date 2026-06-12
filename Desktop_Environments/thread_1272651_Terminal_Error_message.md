---
title: "Terminal Error message"
date: 2009-09-22
forum: Desktop Environments
---

### Post by laud on 2009-09-22
I tried opening my Terminal and the ff error message come up : 
**There was an error creating the child process for this terminal**.

after this you can not type into it ............... what could possibly be the problem?????????????

any ideas???????????????????//
[IMG]http://ubuntuforums.org/home/laud/Desktop/Screenshot.png[/IMG]

---

### Post by saj0577 on 2009-09-22
You tried opening terminal how?
Where did the error appear? Because that sounds like an error which appears inside a terminal.



Saj

---

### Post by laud on 2009-09-22
> **saj0577 said:**
> You tried opening terminal how?
Where did the error appear? Because that sounds like an error which appears inside a terminal.



Saj

 i mean the Console Terminal. 
>>>>>>> application>accessories>Terminal
the error message appears in a different window

---

### Post by arrange on 2009-09-22
What's the output of (looking at the child processes of *gnome-terminal*)```
echo $SHELL
locate gnome-pty
```(you will probably have to do it from the console - Ctrl+Alt+F1, login, type)

---

