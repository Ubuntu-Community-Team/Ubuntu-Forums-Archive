---
title: "I need help with 'top' and 'jobs'"
date: 2009-01-14
forum: General Help
---

### Post by hardysummer on 2009-01-14
I need a command that will output the name of a specific application I am running. 'jobs' would not show the application running if it was started by a script. 'top' occupies an entire terminal.

Is there a way I can get 'jobs' to output an application started by a script or have 'top' output the information and quit? Or another command that gives similar results?

---

### Post by adult swim on 2009-01-14
im not sure if i understand you correctly, but you can monitor one process with top
if you run ```
ps -C program
``` where program is the one you want to monitor and then from the pid that is returned run ```
top -p xxxxx
``` where xxxxx is the pid

---

### Post by kaibob on 2009-01-14
The suggestion by adult swim will hopefully provide what you need. If not, you may want to look at the information provided by ps by entering the following in a terminal window:

```
ps -e
```

Also try:

```
ps ax
```

The ps command shows both a script that is executed and any program started by the script.

---

