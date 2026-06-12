---
title: "Mouse doesn't work"
date: 2006-06-08
forum: Desktop Environments
---

### Post by christooss on 2006-06-08
I got new mouse. it is q-tec wireless optical mouse. ps/2 but mouse isn't recognised by Ubuntu.

This is end of dmesg command output

[4311795.596000] psmouse.c: bad data from KBC - timeout
[4311796.305000] logips2pp: Detected unknown logitech mouse model 0

Any suggestion how to work on this problem?

---

### Post by fmo on 2006-06-08
Hi Christooss,

have you tried to play around with the mouse protocol options in you xorg.conf?

Maybe trying
```
Option "Protocol" "PS/2"
```
or
```
Option "Protocol" "IMPS/2"
```
or
```
Option "Protocol" "ExplorerPS/2"
```

---

### Post by christooss on 2006-06-09
None of those options work.

---

