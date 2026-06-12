---
title: "Shell script always runs Condition 2"
date: 2009-01-17
forum: General Help
---

### Post by thache on 2009-01-17
I've been try trying to get this script to work. Basically I'm trying to get condition 1 to pass but never will becasuse of:
> onoff.sh: 7: [$ONOFF=on]: not found

```
#!/bin/sh
ONOFF='sed -n p1 ~/servoonoff.txt';
if ['$ONOFF'='on']; then
echo "Cond1";echo "off" > ~/servoonoff.txt;
else
echo "Cond2";echo "on" > ~/servoonoff.txt;
fi
```

Contents of servoonoff.txt:
```
on
```
This has been driving me crazy. Any help is appreciated.

---

### Post by unutbu on 2009-01-17
[PHP]ONOFF=$(sed -n 1p ~/servoonoff.txt);
echo $ONOFF
if [ "$ONOFF" = 'on' ]; then
    echo "Cond1";echo "off" > ~/servoonoff.txt;
else
    echo "Cond2";echo "on" > ~/servoonoff.txt;
fi
[/PHP]

Use $(...) around the sed command, lest it will not run.

Place a space after the left bracket [ on line 3. Otherwise, sh will look for a command called [on or [off.

---

### Post by thache on 2009-01-17
It works! Thank you. This is my first time writing a shell script.

---

### Post by maybeway36 on 2009-01-17
"[" is actually a command located in /usr/bin, which is why it needs a space.

---

