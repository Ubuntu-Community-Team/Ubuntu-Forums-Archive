---
title: "unmute master playback at start up"
date: 2009-05-25
forum: Desktop Environments
---

### Post by forum4programs on 2009-05-25
[SOLVED]

hi,


Each time I restart xubuntu, my Master playback is mute. So it is necessary for me unmute it at start up.

I try to unmute master playback at start up by adding this command line "amixer set Master playback unmute" to "Application Autostart" (Applications => Settings => Session and Startup => Application Autostart). I know that the command line works, but I don't know why the program doesn't execute that command line.

Currently I have to execute it by hand which is not very practical.

Using Xubuntu 9.04

---

### Post by kpkeerthi on 2009-05-25
Change it to:
```
 bash -c "amixer set Master playback unmute"
```
and see if it helps

---

### Post by forum4programs on 2009-05-25
> **kpkeerthi said:**
> 
```
 bash -c "amixer set Master playback unmute"
```


It doesn't help :(

---

### Post by forum4programs on 2009-05-25
hmmmm.... Maybe I found a possible workaround, but I don't know how to countdown.

pseudocode:

wait_for(5 seconds) ; execute command1 ; execute command2 ; .....

---

### Post by forum4programs on 2009-05-25
YESSSS!!! FINALLY!!!

my solution is this command: bash -c "sleep 15 ; amixer set Master playback unmute"

xfce4-mixer command execute AFTER my "amixer set Master playback unmute"-command. That is the problem. So I have to wait for about 15 seconds.

kpkeerthi, thanks for "bash -c" information. Else I don't know how to execute commands in series.

---

