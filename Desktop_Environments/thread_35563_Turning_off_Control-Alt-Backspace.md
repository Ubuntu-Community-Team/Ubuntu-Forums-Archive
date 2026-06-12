---
title: "Turning off Control-Alt-Backspace"
date: 2005-05-19
forum: Desktop Environments
---

### Post by skagedal on 2005-05-19
Hi!

Is there a way I can turn off Control-Alt-Backspace killing my X? Or change the key combination?

On my keyboard (Kinesis) it is very easy to hit this combo by mistake. 

Greetings,
Simon

---

### Post by Sam on 2005-05-19
[QUOTE=skagedal]Hi!

Is there a way I can turn off Control-Alt-Backspace killing my X? Or change the key combination?

On my keyboard (Kinesis) it is very easy to hit this combo by mistake. 

Greetings,
Simon[/QUOTE]
[http://www.ubuntuforums.org/showthread.php?t=28625](http://www.ubuntuforums.org/showthread.php?t=28625)

---

### Post by nad on 2005-05-19
In your /etc/X11/xorg.conf files ServerFlags section, uncomment or add line ' Option "DontZap" '

---

### Post by skagedal on 2005-06-11
A bit late, but thank you very much for helping!

---

