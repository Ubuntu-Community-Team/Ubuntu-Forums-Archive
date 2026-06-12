---
title: "Lost the top of my windows"
date: 2009-03-15
forum: Desktop Environments
---

### Post by freddie3782 on 2009-03-15
install compiz from the add and remove application and 
activated some stuff. now I cant get a task bar on top of my windows
where I can close the window or access the File button and Edit and so
forth. So I cant close any window and my right click does not work anymore
Can any one help?

---

### Post by ajgreeny on 2009-03-15
Can't specifically help with the compiz problem, but can hopefully get rid of it temporarily for you, then you can look into the problem further.
Hit Alt+F2 to get a run dialog box and type ```
metacity --replace
``` and hit enter.  You should now be back to using the default gnome window manager and should be able to see everything again, and investigate your problem further.

It might help to tell us more about your hardware, as it could give us a clue about the problem.

---

### Post by freddie3782 on 2009-03-15
ALT + F2 DON'T WORK PRESSED IT NOTHING HAPPENED.
i DON'T WANT TO RETURN TO WINDOWS SOMEONE HELP!

---

### Post by freddie3782 on 2009-03-15
HOW CAN I OPEN run dialog box FROM THE TERMINAL?

---

### Post by zhocchao on 2009-03-15
i am not sure (I tried compiz, but I don't like it), try installing emerald, or try
emerald --replace
you can do it in a terminal

---

### Post by tr33m4n on 2009-03-15
If you wish to run that command from the terminal, simply type:

```
metacity --replace
```

and press enter... that should restore your window borders and as ajgreeny said, give a chance to work out the problem.

If the problem is with compiz, do not install Emerald as suggested by zhocchao. Emerald uses compiz to render its window decorations, and therefore won't help you solve the 'missing' border problem.

Hope this helps,
Cheers
Dan

---

