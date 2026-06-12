---
title: "Firefox Bash Scripting"
date: 2009-02-11
forum: General Help
---

### Post by thunderduck3141 on 2009-02-11
Hey all,

I need to make a script that opens an instance of firefox, leaves it open, then after X minutes closes it, and then repeats the whole process until the user sends a kill signal of some kind.

If anyone could give me a hand Id very much appreciate it.
For those of you wondering it's for a home network stress test of sorts.

Best,
The Duck

---

### Post by thunderduck3141 on 2009-02-12
Anyone?

---

### Post by SOpsMattW on 2009-03-21
maybe something like


```

#! /usr/bin/bash
while true
do
    #launch url in firefox
    firefox <url>

    # wait 2 min (in seconds)
    sleep 120

    #kill all instances of firefox
    killall firefox

done

```

---

### Post by ghostdog74 on 2009-03-21
what is the purpose of doing such a thing. just curious

---

### Post by KeyserSoze93 on 2009-03-21
```
firefox http://www.site.com & pid=$! ; sleep 20s && kill $pid
```

Open firefox in the background, sets $pid to $! (the PID of the last backgrounded process), sleeps 20 seconds, and kills $pid.

---

