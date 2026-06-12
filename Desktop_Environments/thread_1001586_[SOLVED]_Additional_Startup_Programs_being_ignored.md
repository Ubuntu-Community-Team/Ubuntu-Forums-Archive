---
title: "[SOLVED] Additional Startup Programs being ignored (Ibex)"
date: 2008-12-04
forum: Desktop Environments
---

### Post by rimbaud on 2008-12-04
Hello all

My "Additional startup programs" in "Sessions Preferences" is being ignored after upgrading to Ibex, but worked fine in Hardy.

The "remember currently running applications" doesn't seem to do anything for me either.

Any suggestions?

Thanks in advance

---

### Post by gjoellee on 2008-12-04
tried using the gconf-editor? can't describe it to you so good now becuase I am a school and using windows :o
```
gconf-editor
```

---

### Post by rimbaud on 2008-12-09
I'm not sure where to look in there.  Also some programs are KDE ones and they started fine in Hardy.

---

### Post by habtool on 2008-12-09
Under sessions, make sure that the file name you are using is in fact still the same in /usr/bin/
It may be a idea to link direclty to the binary file, as in:
/usr/bin/miro   , as a example, so use the browse and click the actual executable file that you want to run.

Also open a terminal and run the command you trying to start in sessions and make sure that it can infact run without errors.


Also as far as I know there is a bug in "remember currently running applications", so this is simply not working.


good luck

---

### Post by rimbaud on 2008-12-12
Thanks for the advice .  I fixed this: I deleted all the files in ~/.config/autostart/ and unchecked all the items in "Additional startup programs" and then re-added or re-checked my extra startup programs.

Problem solved.

---

