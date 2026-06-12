---
title: "Ubuntu Task Manager?"
date: 2009-01-28
forum: General Help
---

### Post by RedSingularity on 2009-01-28
Is there a series of buttons i can push if my window freezes up in Ubuntu?  I know in windows i Ctl+ALt+Del and it brought me to the task manager.  Is there something similar with ubuntu?

---

### Post by pedro_orange on 2009-01-28
Not really. If you just want to kill a process you can do the following:

If a certain process dies, I just open a terminal and do a grep on the processes running. 

Something like:

```
sudo ps -aux | grep progam-name
```
or
```
pregp program-name
```

Then once I've found the process ID, I'll kill it with the command:

```
sudo kill -9 ######
```

The #'s being the process id.

---

### Post by binbash on 2009-01-28
ctrl + alt + backspace

---

### Post by mb_webguy on 2009-01-28
The System Monitor is close to the Task Manager in that it shows in formation about your computer including running processes and system resources.  The System Monitor can be opened by going to System->Administration->System Monitor, or by adding the System Monitor applet to your panel.

Various terminal commands are also available to display this information, kill processes, etc.

If you're having problems with applications, graphics, or other similar areas, you can restart your X session with Ctrl-Alt-Backspace.  And just like in Windows, you can restart your computer with Ctrl-Alt-Delete.

---

### Post by sandyd on 2009-01-28
in kde, press control alt delete (kde 3)
it works, just like in windows .
look out for the small menu that comes out on the top left corner of screen

---

