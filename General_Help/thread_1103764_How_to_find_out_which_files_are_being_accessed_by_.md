---
title: "How to find out which files are being accessed by Firefox as it runs"
date: 2009-03-23
forum: General Help
---

### Post by Endolith on 2009-03-23
After using Firefox for a while, it will start to lock up for seconds at a time every few seconds.  It hogs the processor, and when I shut it down, it continues to use 100% CPU indefinitely after the window has closed.  How can I find out what it's doing?

---

### Post by hyper_ch on 2009-03-23
lsof gives you a list of current open files. don't know how to limit it to ff only.

---

### Post by Endolith on 2009-03-23
> **hyper_ch said:**
> lsof gives you a list of current open files. don't know how to limit it to ff only.

You'd use this:

```
lsof | grep firefox
```But I'm not sure what I'm supposed to do with that.

---

### Post by Yashiro on 2009-03-23
Sounds like you're running a 32bit Flash or java plugin on a 64bit system.

---

### Post by Endolith on 2009-03-23
> **Yashiro said:**
> Sounds like you're running a 32bit Flash or java plugin on a 64bit system.

No.  32 bit system

---

### Post by geirha on 2009-03-23
To see what files firefox currently has open, first find the pid of firefox
```
pidof firefox
```
Then use that pid with the lsof command. If the pid is *1234*, then
```
lsof -p *1234*
```

---

### Post by Endolith on 2009-03-23
> **geirha said:**
> To see what files firefox currently has open, first find the pid of firefox
```
pidof firefox
```Then use that pid with the lsof command. If the pid is *1234*, then
```
lsof -p *1234*
```

How is that any different from lsof | grep firefox?

---

### Post by geirha on 2009-03-23
> **Endolith said:**
> How is that any different from lsof | grep firefox?

It only shows the files open by firefox. The one with grep will also show other processes if they have open a file with firefox somewhere in the path.

---

### Post by Endolith on 2009-03-23
> **geirha said:**
> It only shows the files open by firefox. The one with grep will also show other processes if they have open a file with firefox somewhere in the path.

Ok, but how does this help me find out which files it's writing to right now so I can figure out what's causing it to slow down?

---

