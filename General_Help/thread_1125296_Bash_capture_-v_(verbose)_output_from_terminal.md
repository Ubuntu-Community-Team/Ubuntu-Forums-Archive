---
title: "Bash: capture -v (verbose) output from terminal"
date: 2009-04-14
forum: General Help
---

### Post by prem1er on 2009-04-14
I have a simple bash script that makes a call to another process.  I have no knowledge of what the process is doing in the background, but when I run it in verbose mode I get a very nice output (to the terminal) of what is happening.  I would like to redirect this output to a log file. I have been reading about how to do this redirection, but it doesn't seem to be working for me.  The -v option always prints to the screen.  I have been using this at the end of the call to the process...

```
>> log.text 2>&1
```

---

### Post by prem1er on 2009-04-14
Nevermind, that was a dumb mistake I put that line underneath my call to the process instead of on the same line.  Here is what I was trying to do in case anyone is wondering.

```
arsdoc update -u admin -p $1 -h localhost -i "where acctnum='$TMMS'" -n "acctnum='$SEI'"
-G "xxxx" -f"xxxx" -v >> log.txt 2>&1
```

---

