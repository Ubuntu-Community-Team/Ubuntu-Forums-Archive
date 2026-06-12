---
title: "Terminal not coming up on Ubuntu 16.04"
date: 2016-10-01
forum: Desktop Environments
---

### Post by jj.wauters on 2016-10-01
Since my last Ubuntu update yesterday I cannot open Terminal anymore.
It comes up and disappears immediately.
Same if I try to open with Ctrl+Alt+t or open with UTerm or UxTerm.

Any idea how to fix???

---

### Post by howefield on 2016-10-01
Vanilla Unity desktop environment ?

What is the output from uterm/uxterm when you try to open terminal, you might get some clues in ~/.xsession-errors.

---

### Post by jj.wauters on 2016-10-01
Don't know what you mean by Vanilla, but it concerns a Ubuntu 16.04 install out of the box.
The terminal rectangle is popping up during less than a millisecond and then it's gone.
.xsession-errors contains next 2 lines :
openConnection: connect: No such file or directory
cannot connect to brltty at :0

---

### Post by jj.wauters on 2016-10-02
In the meantime, I tried to solve by removing Gnome-Terminal in Software center, and reinstalling afterwards.
Same result.
Please can anybody help???

---

### Post by oldos2er on 2016-10-02
Did you try howefield's suggestion of trying to run xterm? Try Alt-F2, type in *xterm*

---

### Post by jj.wauters on 2016-10-02
Sorry, in my first question I said "Same if I try to open with Ctrl+Alt+t or open with _**UTerm** or UxTerm_."
It should be "_**XTerm** or UxTerm"_
So none of them are working. On the other hand there is no problem to open any other application. It's only related to the Terminal window, and that's really very annoying.
Is there anywhere a config file that I can modify or replace by a copy from a backup (unfortunately still in 14.04LTS) ?

---

### Post by &amp;KyT$0P# on 2016-10-02
What happens if you hit Ctrl-Alt-F1 and login from there?  (If it works, enter [FONT=Courier New]exit[/FONT] to get out.)

Ctrl-Alt-F7 to go back to your desktop.

---

### Post by howefield on 2016-10-03
To get back to a default bashrc file you could take a copy of the current file

```
cp ~/.bashrc ~/Documents/.bashrc.bak
```

and then recreate a fresh bashrc file with..

```
cp /etc/skel/.bashrc ~/
```

I've a feeling this won't be the solution but worth trying the easy stuff first.

---

### Post by jj.wauters on 2016-10-03
Fantastic. It works.
Many thanks

---

### Post by howefield on 2016-10-03
Cool, glad you got it, if you created the backup copy of the .bashrc file you can delete it if all is well now

Feel free to mark the thread as solved :)

---

