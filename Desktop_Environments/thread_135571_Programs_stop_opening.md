---
title: "Programs stop opening"
date: 2006-02-24
forum: Desktop Environments
---

### Post by Conie on 2006-02-24
Firstly, I'd just like to say that I've been running (and loving) Ubuntu for about two months now.
Only a few days after installation, I did notice one peculiar problem. After a while of running, the computer starts to refuse to open programs. All I get is 'Starting Whatever' in the bottom bar (e.g, 'Starting Firefox Web Browser'). It stays around for a few seconds, then it disappears, and nothing more happens. In some cases, I get nothing at all. If I close some programs I can usually open another, but eventually after closing all the programs I'm willing to go without all that I can do is restart x windows, a rather ugly solution.

I've searched around, but without any clear errors or even any idea as to what is really happening, it feels like I'm searching for a very small needle in a huge haystack. Any insight or advice would be greatly appreciated.

---

### Post by cskeide on 2006-02-24
try starting the program from a terminal. this way you'll see the error messages.

---

### Post by lamego on 2006-02-24
Give a look into your system log:
/var/log/messages

---

### Post by taurus on 2006-02-24
May want to look at your error log in ~/.xsession-errors,

less ~/.xsession-errors

---

