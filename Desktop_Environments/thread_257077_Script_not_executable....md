---
title: "Script not executable...?"
date: 2006-09-14
forum: Desktop Environments
---

### Post by GabrielWolff on 2006-09-14
Hey, I downloaded a script, *cueape.sh*, put in in my /usr/bin folder, made it executable by ```
sudo chmod -x cueape.sh
```, and when I try to execute it with no root rights, I'm gettin: ```
gabriel@gabriel:~$ cueape.sh
bash: /usr/bin/cueape.sh: Permission denied
gabriel@gabriel:~$

``` Sounds plausible.
Only when then I want to use this script with sudo, it suddenly doesn't exist anymore:```
gabriel@gabriel:~$ sudo cueape.sh
sudo: cueape.sh: command not found
gabriel@gabriel:~$
```

What happened? I'm sure it's something really simple, I just can't see what.

G

---

### Post by Jussi Kukkonen on 2006-09-14
> I'm sure it's something really simple, I just can't see what.
:)

```
sudo chmod **+**x cueape.sh
```

---

### Post by nrwilk on 2006-09-14
Yeah, the command you'd issued actually *removed* the script's execution privileges. Use the command which Jussi suggested.

I'm not sure why the script isn't seen when executed as root.  Try making it executable and see if that helps first.

nrwilk

---

### Post by GabrielWolff on 2006-09-14
> **Jussi Kukkonen said:**
> :)

```
sudo chmod **+**x cueape.sh
```

Bingo :-)

Thanks

Gabriel

---

