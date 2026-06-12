---
title: "What do all of these killall commands mean mean?"
date: 2006-01-25
forum: Desktop Environments
---

### Post by ardchoille on 2006-01-25
I have seen killall -9, killall -15, killall -HUP. What are all these killall arguments and where can I read about what each one does? If there is a killall -9, does that mean there is also a killall -1, killall -2, killall -3, etc?
I tried man killall but that doesn't give any useful information about my query.

---

### Post by RAOF on 2006-01-25
[QUOTE=ardchoille]I have seen killall -9, killall -15, killall -HUP. What are all these killall arguments and where can I read about what each one does? If there is a killall -9, does that mean there is also a killall -1, killall -2, killall -3, etc?
I tried man killall but that doesn't give any useful information about my query.[/QUOTE]
The killall -9,-15,-HUP switches are the signal to send to the program you're trying to kill.  Looking at the info page of kill (info coreutils kill) shows that:
```
`HUP'
     1.  Hangup.

`INT'
     2.  Terminal interrupt.

`QUIT'
     3.  Terminal quit.

`ABRT'
     6.  Process abort.

`KILL'
     9.  Kill (cannot be caught or ignored).

`ALRM'
     14.  Alarm Clock.

`TERM'
     15.  Termination.

```man killall would have referred you to kill (among other 'see also's).  If you don't know what the signals mean, you don't need to care.

---

### Post by ardchoille on 2006-01-25
[QUOTE=RAOF]... If you don't know what the signals mean, you don't need to care.[/QUOTE]
Ah, ok, thank you.

---

