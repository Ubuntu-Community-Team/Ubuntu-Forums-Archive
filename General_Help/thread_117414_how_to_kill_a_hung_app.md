---
title: "how to kill a hung app?"
date: 2006-01-14
forum: General Help
---

### Post by sagittarius on 2006-01-14
newbie question ... I can't find the answer in the documentation ... what is the equivalent of Ctrl-Alt-Del - End Process in Linux please :?

---

### Post by ed_d on 2006-01-14
If completely locked, try ctrl-alt-backspace

If can open a terminal, ps -ef | grep <name of prosess you were running> find its "job number" then sudo kill -9 <job number>

---

### Post by aysiu on 2006-01-14
You could also try Alt-F2 and ```
xkill
```

---

### Post by sagittarius on 2006-01-14
WOW!!! that was quick!  thx so much to you both :D

---

### Post by jasmuz on 2006-01-14
In the programs menu--->System Tools--->System Monitor

In the console:

ps aux | grep program name 
and then,
sudo kill -9 idnumber

---

### Post by sagittarius on 2006-01-14
and thx again, jasmuz :D

---

