---
title: "Vista And Linux..."
date: 2008-09-23
forum: Desktop Environments
---

### Post by SilverCrow on 2008-09-23
hi guys i have vista and linux dual booting ithink it doesnt concern my problem

anyway i have ubuntu when i logged in vista then afte a while i logged on linux but after i logged in linux by 5 min it lags and freeze i cant do anything exept hit the shutdown button so like that i only have vista linux lag at me and this problem happened at me when i shutted down linux then it lag why??

---

### Post by lian1238 on 2008-09-24
When it freezes, don't hit the power button. Instead, hold Alt and SysRq (PrtSc) and type the follow letters: R, E, I, S, U, B, leaving about 1 or 2 seconds in between. This is the safer way to reboot.

As for the freezing, can you press Ctrl+Alt+Backspace to restart X? Or Ctrl+Alt+F1 to go to the terminal? Next time it freezes, try pressing Ctrl+Alt+F1 and you'll be at the terminal, assuming you could. Login. Then type "top" (no quotes). You'll see the processes that are using the most CPU time and memory. Remember the PID of the one which is taking up lots of CPU. Then type "kill <PID_of_that_process>".

---

