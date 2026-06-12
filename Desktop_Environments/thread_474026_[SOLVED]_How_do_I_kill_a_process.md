---
title: "[SOLVED] How do I kill a process?"
date: 2007-06-14
forum: Desktop Environments
---

### Post by CaptainSteel on 2007-06-14
Im trying to kill a process in Kubuntu and im not getting any luck. I keep getting this error. "Insufficient permissions to kill process" xxxxx. Is there any way to terminate, kill, or stop a process in the GUI or does it have to be done by command line? Thanks.

---

### Post by bukwirm on 2007-06-14
Are you trying to kill the process as root (ie, using sudo)?

---

### Post by CaptainSteel on 2007-06-14
No i was trying to kill it using the GUI. I typed ctrl+alt+del and it brought up a menu but wont let me kill any processes i keep getting the same error.

---

### Post by ykpaiha on 2007-06-14
have you tried xkill in a console then clic on the opened windows
you have as well in system monitor the way to close any open processus
good luck

---

### Post by trippinnik on 2007-06-14
you should just use the kill command from the terminal.  If you want a good list of the processes and how much CPU they're using type "sudo top" then if you want to kill a process press 'k' and the process ID when prompted.  You can also give programs more or less Priority by typing 'r'.

---

### Post by ynnhoj on 2007-06-14
an easy way to find a list of processes is to run the command:
```
ps -A
```
make a mental note of the process id (the left-most column of numbers) and use the kill command:
```
kill ####
```
if you you find you don't have sufficient permissions, then use sudo ("sudo kill ####").

note: the "kill" command was unfortunately not given the best name -- it simply is used to send a signal to a process.  you don't necessarily have to send the kill signal (though that is the *default* action).  you can read more about kill and signals in the man page ("man kill").

---

