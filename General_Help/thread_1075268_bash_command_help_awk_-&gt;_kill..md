---
title: "bash command help awk -&gt; kill."
date: 2009-02-20
forum: General Help
---

### Post by yeleek on 2009-02-20
Hi,

I have multiple conky scripts running which work great, but sometimes I want to be able to close them all in one sweep.

This

ps -A | grep "conky" | awk '{print $1}'

Does get me the pid of all the running conky instances.  How can I pass it so that Kill is run against all of them (probably 3 instances for what its worth).

Thanks

---

### Post by geirha on 2009-02-20
There's the killall command for that. ```
killall /usr/bin/conky
```

---

### Post by yeleek on 2009-02-20
That is indeed a far easier method of doing it - Thanks :)

Out of interest, is it possible to do what I'm asking?

---

### Post by geirha on 2009-02-20
Yes. Either with the command substitution feature of the shell, or with xargs
```
# Command substitution:
kill $(ps -A | grep "conky" | awk '{print $1}')
# or
kill `ps -A | grep "conky" | awk '{print $1}'`
# xargs:
ps -A | grep "conky" | awk '{print $1}' | xargs kill

```

---

### Post by yeleek on 2009-02-20
Thats great - many thanks :)

---

### Post by geirha on 2009-02-20
Oh and btw. ```
ps -A | grep "conky" | awk '{print $1}'
```
awk also has the capability of doing what grep does in this case, so you could shorten the command down to:
```
ps -A | awk '/conky/{print $1}'
```

---

### Post by yeleek on 2009-02-20
wow didn't know that - thanks :)

---

