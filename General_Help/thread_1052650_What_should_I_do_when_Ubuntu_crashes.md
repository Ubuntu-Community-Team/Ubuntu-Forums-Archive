---
title: "What should I do when Ubuntu crashes?"
date: 2009-01-27
forum: General Help
---

### Post by airjaw on 2009-01-27
Hey guys, I'm getting a bit fed up with being helpless when ubuntu crashes on me. Usually the culprit is a firefox page that will just freeze my entire system. I can still move my mouse and I can even hear my music still playing, but I can't do anything else.
Are there any keyboard shortcuts I can call? CTRL ALT Backspace doesn't work.  I don't think CTRL ALT F1 worked either.

Also, is there some log file i can look at that can give me more insight into what happened? I just want to be proactive about this and hopefully help ubuntu so that these bugs occur less frequently.

---

### Post by Boomhauer on 2009-01-27
try hitting alt+f2 and entering in ```
killall firefox
```
you could launch firefox from a terminal and when it crashes look at the terminal and see if there are errors displayed.

---

### Post by Saghaulor on 2009-01-28
Word I've been having a similar problem.

I'm using Ubuntu 8.1, installed via Wubi.

Firefox, with flash-nonfree, adblock plus.

To confirm, ctrl alt F1 is useless, as is ctrl alt backspace.

Is there anything left to do aside from hard reboot?

---

### Post by xeth_delta on 2009-01-28
> **airjaw said:**
> Hey guys, I'm getting a bit fed up with being helpless when ubuntu crashes on me. Usually the culprit is a firefox page that will just freeze my entire system. I can still move my mouse and I can even hear my music still playing, but I can't do anything else.
Are there any keyboard shortcuts I can call? CTRL ALT Backspace doesn't work.  I don't think CTRL ALT F1 worked either.

Also, is there some log file i can look at that can give me more insight into what happened? I just want to be proactive about this and hopefully help ubuntu so that these bugs occur less frequently.

If what boomhauer does not work, you have several alternatives:
using ps and locating the process id (PID), second column:
```
ps -ef | grep -i proces_name
```
in your case, firefox. once you got the PID_nr of the firefox process, you can kill it with:
```

kill -9 PID_nr
```

Another option is using "top", locating the offending process, marking it with the cursor, pressing "k" and indicating how it should be killed, 9 is a good choice.
```
top
```
to quit top, simply press "q".

Yet another option is to use a graphical interface for process management. For example System Monitor in KDE. I am not sure what the name is in Gnome, but I assume it would be something similar.

It might be possible to also call xkill with Control+Alt+Escape

You can find system logs in /var/log/ and maybe some error logs info in .mozilla for firefox.

Good luck!

---

### Post by PocketDog on 2009-01-28
Launching Firefox from Terminal as recommended above is definitely the way to go. That'll help find a cure. Another temporary solution is to right click your panel - add to panel - add 'force quit'. When you click it your pointer changes, and you then click on any window of a process you want to kill.

---

### Post by dhughes on 2009-01-28
> **xeth_delta said:**
> ...

Yet another option is to use a graphical interface for process management. For example System Monitor in KDE. I am not sure what the name is in Gnome, but I assume it would be something similar...

 Yes it is the same in GNOME, it's also called System Monitor.

 I have it added to a panel so I can see if some process has gone nuts and is so busy it seems as if nothing else is working.

---

### Post by airjaw on 2009-01-28
Thanks guys..
(Just compiling all the options into one helpful list)

Alt+F2
```
killall firefox
```

It might be possible to also call xkill with 
**Control+Alt+Escape**

Start firefox from terminal

Check /var/logs

I don't believe any shortcuts work. I can't get a terminal open during the freeze. I checked /var/logs after i rebooted and it didn't have anything written during the time that firefox crashed.
I'll just have to open firefox with a terminal next time. If i want to open new windows of firefox, should I keep opening in terminal or is only the initial start of the first firefox window in terminal necessary?

Thanks.

---

### Post by Crafty Kisses on 2009-01-28
What are your system specs?

---

### Post by airjaw on 2009-02-23
Ubuntu 8.10 32-bit

Dell Inspiron 1520 Laptop
2.2ghz Core2Duo
4GB RAM

---

