---
title: "Problem with GREP &quot;freezing&quot;"
date: 2008-12-15
forum: General Help
---

### Post by uvdevnull on 2008-12-15
```
$sudo grep -rl "string" /
```
Results in listing several files in the /etc directory, then a few permission denied lines at the /proc level (expected) but then just sits there for days without doing anything. HTOP shows 0.0 CPU% and the CPU time is not incrementing beyond the few seconds it used at the beginning of the run.

The same occurs when I start the search at /usr.

Thanks,
uvdevnull

---

### Post by pennacook on 2008-12-15
You might want to throw it into the background (ctrl-z and then bg) and then run an strace to see what it is stuck reading. Likely trying to find the "string" in some large binary file(s).

```
sudo strace -aef -p <PID>
```

---

### Post by uvdevnull on 2008-12-15
I even tried running grep with the -I option to exclude binary files and still the same result.  Same exact result with the ack-grep utility.

When I ran the trace per your suggestion, I get the same result from both commands:

```
Process 23665 attached - interrupt to quit
read(3, ^C <unfinished ...>
Process 23665 detached
```

It just sits there after "read(3, " without any further output until Ctrl-C.

---

