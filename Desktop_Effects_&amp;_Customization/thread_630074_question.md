---
title: "question"
date: 2007-12-02
forum: Desktop Effects &amp; Customization
---

### Post by bigearl on 2007-12-02
id like to know if linux has something like windows ctrl+alt+del because i got stuff thats frozen and wont close untill i reboot

---

### Post by santiagoward2000 on 2007-12-02
> **bigearl said:**
> id like to know if linux has something like windows ctrl+alt+del because i got stuff thats frozen and wont close untill i reboot

Hi!
When nothing is responding and you want to reboot your computer safely, you have to press (are you ready?)
```
Alt+PrtSC+R+S+E+I+U+B
```
Each letter at a time and with some time between one and the next.
You can read more about it on this thread:
[http://ubuntuforums.org/showthread.php?t=617349&highlight=elephants]("http://ubuntuforums.org/showthread.php?t=617349&highlight=elephants")

---

### Post by spiff95 on 2007-12-03
> **santiagoward2000 said:**
> Hi!
When nothing is responding and you want to reboot your computer safely, you have to press (are you ready?)
```
Alt+PrtSC+R+S+E+I+U+B
```
Each letter at a time and with some time between one and the next.
You can read more about it on this thread:
[http://ubuntuforums.org/showthread.php?t=617349&highlight=elephants]("http://ubuntuforums.org/showthread.php?t=617349&highlight=elephants")

If everything is locked up you can also hold ctrl+alt down and press F6 to get a text login and then run:

sudo shutdown now

If it's just a couple of processes that won't work (and you can pull up a terminal), open terminal and type:

sudo ps 

if you KNOW which processes are the culprits, you can issue a kill command. But it would be safer to just execute a safe reboot and start again.

---

