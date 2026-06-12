---
title: "[SOLVED] open applications and files with the terminal"
date: 2008-12-11
forum: General Help
---

### Post by bryncoles on 2008-12-11
ok, should just be a quickie this... 

i know how to open a file with the terminal using a command like (say) 

```
gedit ~/Desktop/bob
```

to open the file 'bob', stored on the desktop. this renders the terminal 'occupied' until i close bob however. what switch do i need to use so that the already open terminal can be used for other tasks without closing bob?

also: anyone know how to make the terminal open in the desktop, rather than in the home folder?

cheers!

---

### Post by ettercap on 2008-12-11
use an ampersand symbol after the whole statement that shuold do the work.

like

         " gedit /user/Desktop/file.txt & "

---

### Post by nielz on 2008-12-11
If you forget the ampersand you can also press ctrl-z (suspend) and then type bg (to have it run in the background). You can also type "jobs" to list currently running jobs. Finally you can use the fg command to bring a taks running in the background to the foreground again. For more info try typing: help fg, help bg or help jobs.

```

nielz@box:~$ gedit
^Z
[1]+  Stopped                 gedit
nielz@box:~$ bg
[1]+ gedit &
nielz@box:~$ jobs
[1]+  Running                 gedit &

```

Linux is awesome :)

---

### Post by bryncoles on 2008-12-11
spot on! thats (in both cases) exactly what i wanted to know! cheers guys!

---

