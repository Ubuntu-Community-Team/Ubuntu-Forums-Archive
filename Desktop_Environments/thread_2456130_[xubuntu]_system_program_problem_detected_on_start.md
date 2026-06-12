---
title: "[xubuntu] system program problem detected on startup ..."
date: 2021-01-05
forum: Desktop Environments
---

### Post by dbee on 2021-01-05
Searched this forum and read some online tutorials but can't seem to get rid of this issue on xubuntu (latest) on startup.

I get a modal box on startup with 'system program problem detected'.

Online tutorial said it was a crash issue and that i should delete */var/crash/**. Thing is though, /var/crash is an empty directory on my system.

Had a look at syslog, can't find anything useful in there...

System froze a while back and i had to power off. Probably an issue with that crash i'd imagine.

---

### Post by ActionParsnip on 2021-01-05
Does the system work, despite the message ?

---

### Post by T6&amp;sfpER35% on 2021-01-05
what does ```
ls -l /var/crash/
``` show ?

---

### Post by dbee on 2021-01-05
system works fine ...

```

dara@dara-HP-Stream-Laptop-11-y0XX:~$ ls -l /var/crash
total 0

```

---

### Post by T6&amp;sfpER35% on 2021-01-05
weird , "system program problem detected" is just a notification of a [crash in the system](https://itsfoss.com/how-to-fix-system-program-problem-detected-ubuntu/)[COLOR=#000000]...but your crash log shows nothing.
i'm afraid i can't contribute to this thread anymore ,sorry .
will keep en eye on this one to see the solution lol[/COLOR]

---

### Post by dbee on 2021-01-06
so this morning when i logged on. The message didn't show up.

it's possible that i deleted the crash log unintentionally yesterday and that fixed it.

Or it might be a case of xubuntu giveth, xubuntu taketh away. Who knows. 

I'm going to mark this thread as solved since deleting the crash log is probably the solution.

```

dara@dara-HP-Stream-Laptop-11-y0XX:~$ sudo rm -rf /var/crash/*

```

Also does anyone else take precautions when working with *rm -rf* ? I usually take an *rm* in stages to prevent a slip of the finger deleting something important on my system...

so basically i type

```

-rf /mydir/myfile

```

then i finish it off with an *rm*

```

rm -rf /mydir/myfile

```

this goes double when I'm working with the match all *** operator.

is this just a *me* thing or does anyone else do this as well?

---

