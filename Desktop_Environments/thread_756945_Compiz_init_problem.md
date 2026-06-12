---
title: "Compiz init problem"
date: 2008-04-16
forum: Desktop Environments
---

### Post by Triggerhapp on 2008-04-16
I have an interesting question to ask about Compiz...
I have a startup script to run only the programs I want, at bootup. Some of them require others to be there first.
If I run "Compiz"(note: no ampersand) first, then it hangs there and the rest of the programs that require it do not run.
If i run "Compiz&" then it drops it into the background, and runs the next program too soon, and it fails to load.
Ok.... so
```

Compiz &
(sleep 5 ; otherprogram) &

```
This works. First login on a boot, it runs compiz, compiz finishes loading, i get my other program run...
Next boot, compiz runs in milliseconds, and I wait blankly for 5 seconds for my other app to load.
Is there a way to check if a program has finished loading and started running? May be a dead end but I was asking just incase.
Thanks for those who bothered to read this far :D

---

