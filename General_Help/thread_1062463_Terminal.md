---
title: "Terminal"
date: 2009-02-06
forum: General Help
---

### Post by RedSingularity on 2009-02-06
Lets say i want to go to a Directory and then run a program in that directory.  I know i do "cd /user/home/xxxx" then when i am in that directory i can run the desired program.  How can i do this in one command line tho?

---

### Post by taurus on 2009-02-06
```
/home/username/xxx/filename
```

---

### Post by m_duck on 2009-02-06
To execute *programname *in your home directory, just enter ```
/home/user/programname
```That will run the program if it is executable.

If not, make it executable with ```
chmod +x /home/user/programname
```(or right click the executable and tick the box in he permissions tab.)

EDIT: Aw, too slow.

---

### Post by RedSingularity on 2009-02-06
Ok and what can i do if the folder i am trying to get to has a space in it?  For example, /home/user/.wine/drive_c/**Program Files**.  <<<<<

---

### Post by taurus on 2009-02-06
```
/home/user/.wine/drive_c/"Program Files"/filename
```

or

```
/home/user/.wine/drive_c/Program\ Files/filename
```

---

### Post by RedSingularity on 2009-02-06
Perfect.  Thanks  a lot guys.  :)  :)

---

### Post by andrewc6l on 2009-02-07
Incidentally, on most shells the Tab key is a completion character. So instead of typing all of:
/home/user/.wine/drive_c/Program\ Files/filename

you could type:
/ho[Tab]user/.wi[Tab]/dr[Tab]/Pro[Tab]/file[Tab]

The tab completion will fill in the spaces for you automatically. If you have more than one match, pressing Tab twice brings up a list.

[http://en.wikipedia.org/wiki/Command_line_completion](http://en.wikipedia.org/wiki/Command_line_completion)

---

