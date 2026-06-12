---
title: "Thunderbird close after load"
date: 2006-06-17
forum: Desktop Environments
---

### Post by lepre on 2006-06-17
i don't know if this is related somehow...i was fixing the font rendering in xubuntu (i like NON-clear-type-windows-like) and after that when i try to run thunderbird it loads up and when it ends it just close itself.

i tryed to run it from terminal and that's it:
```
lepre@lepreXubuntu:~$ mozilla-thunderbird
DOUBLE-CLICK: 300 --> -1 THRESHOLD: 8 --> -1 /usr/lib/mozilla-thunderbird/run-mozilla.sh: line 131:  4994 Segmentation fault      "$prog" ${1+"$@"}
lepre@lepreXubuntu:~$

```

any help? :-(

---

### Post by lepre on 2006-06-17
can I up this? i cant' read my e-mails :-x :(

---

### Post by lepre on 2006-06-19
i tryed to delete the user-setting-folder and it start up again.
but as i create a new account it crashes again!
i tried to reinstall and the story is the same...the error is always the same ad in my first post  #-o

---

### Post by snt on 2006-06-21
I have the same problem. I found a very stupid and dangerous solution, but at least it is working. Just run thunderbiird as root, or use a sudo(the former one better, if not you have to move your profile to the root's home drectory).

Anyway, maybe here is the solution: [http://forum.html.it/forum/showthread.php?threadid=989656](http://forum.html.it/forum/showthread.php?threadid=989656)

(Unfortunately I do not understand the last reply, maybe you can...)

hope it helps, and please put here the solution if you find it

s

---

### Post by lepre on 2006-06-22
[QUOTE=snt]I have the same problem. I found a very stupid and dangerous solution, but at least it is working. Just run thunderbiird as root, or use a sudo(the former one better, if not you have to move your profile to the root's home drectory).

Anyway, maybe here is the solution: [http://forum.html.it/forum/showthread.php?threadid=989656](http://forum.html.it/forum/showthread.php?threadid=989656)

(Unfortunately I do not understand the last reply, maybe you can...)

hope it helps, and please put here the solution if you find it

s[/QUOTE]

he said that he downloaded the bin directly from mozilla.com and it works, but that's strange because on an other machine it works correctly with the ubuntu package.

i'll try that...

---

### Post by lepre on 2006-06-22
ok, it works! :p

[mini-how to]
download thunderbid from here: [http://www.mozilla.com/thunderbird/](http://www.mozilla.com/thunderbird/)
untar where you want
put your old profile in ~/.thundebird (from the old ~/.mozilla-thunderbird)
open the directory you created
double click thunderbird file
done
[/mini-how to]

edit: now when i click a link inside thunderbird it doesn't open an external browser anymore (it does nothing at all). i looked in preferences and config file but didn't find anything usefull-related. any help?

---

### Post by lepre on 2006-06-23
fix founded:
add to pref.js this 2 lines:
```

user_pref("network.protocol-handler.app.http", "/usr/bin/firefox");
user_pref("network.protocol-handler.app.https", "/usr/bin/firefox");

```

:mrgreen:

---

