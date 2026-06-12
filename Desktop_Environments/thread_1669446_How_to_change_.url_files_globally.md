---
title: "How to change .url files globally?"
date: 2011-01-17
forum: Desktop Environments
---

### Post by GrahamM on 2011-01-17
I tried posting to this SOLVED thread, but suspect that was the wrong thing to do!

[http://ubuntuforums.org/showthread.php?p=8393052#post8393052](http://ubuntuforums.org/showthread.php?p=8393052#post8393052)

Basically, the thread shows how to strip the first 2 lines of a text file, but because I have quote a number of folders on the desktop each needing the same treatment, I wondered how to do this in one step. 

I figure I might learn something rather than just do the grunt work of switching from folder to folder.

---

### Post by Krytarik on 2011-01-18
How about this command? I puzzled it together from the thread you posted and the some results of a web search:
```
find ~/Desktop -iname "*.url" | xargs sed -i "1,2 d"
```
Greetings.

---

### Post by GrahamM on 2011-01-18
> **Krytarik said:**
> How about this command? I puzzled it together from the thread you posted and the some results of a web search:
```
find ~/Desktop -iname "*.url" | xargs sed -i "1,2 d"
```
Greetings.

Closing this thread - duplicate posting under [All variants]

---

