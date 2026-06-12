---
title: "Linux equivalent of tasklisk / taskkill?"
date: 2006-09-15
forum: Desktop Environments
---

### Post by eggmanpete on 2006-09-15
does anyone know what the equivalent of windowses  tasklisk / taskkill is?

basicly im trying to end a program in terminal.

Thanks

---

### Post by bswilson on 2006-09-15
In a terminal window, use the following command to show all the running processes:

```
$ ps -ef
```

You can also do simply use **ps** to show processes running as the current user.  Then, you can terminate the process with kill:

```
bswilson@doctordre:~$ ps -ef
...
bswilson 32737     1  3 08:58 ?        00:02:14 rhythmbox
bswilson 32761     1  0 08:58 ?        00:00:00 rhythmbox
bswilson  2077     1  0 10:04 ?        00:00:01 gnome-terminal
bswilson  2079  2077  0 10:04 ?        00:00:00 gnome-pty-helper
bswilson  2080  2077  0 10:04 pts/0    00:00:00 bash
root      2185  4794  0 10:07 ?        00:00:00 sshd: root [priv]
sshd      2186  2185  0 10:07 ?        00:00:00 sshd: root [net]
bswilson  2190     1 28 10:07 ?        00:00:01 gedit
bswilson  2191  2080  0 10:07 pts/0    00:00:00 ps -ef
bswilson@doctordre:~$ kill 2190
bswilson@doctordre:~$
```

In this example above, I found the PID (Process ID) for gedit, then I used kill 2190 to terminate gedit.  On my screen, the gedit application closed.  If you want to kill a process that is a service, or running with special permissions, you might have to use** sudo kill <pid>**.

---

### Post by blackened on 2006-09-15
Or if you like doing it from a gui: Alt+F2, then gnome-system-monitor.
This works similar to Windows tasklist. Map this to Ctrl+Alt+Del and off you go.

---

### Post by sethmahoney on 2006-09-15
You can also try 
```
top
```
in the terminal to see the list of processes that are taking the most out of your CPU.

---

### Post by glotz on 2006-09-15
and then there's xkill

---

