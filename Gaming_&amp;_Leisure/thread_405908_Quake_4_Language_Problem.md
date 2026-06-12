---
title: "Quake 4 Language Problem"
date: 2007-04-10
forum: Gaming &amp; Leisure
---

### Post by ZDemon on 2007-04-10
I know this is stupid.

I got Quake 4 for free when i bought my graphic card.

I want to play the game in English. But it is in Spanish or something. I have no idea how or where to change it.

Does anyone have an idea?

---

### Post by rajeev1204 on 2007-04-10
try to locate the file quake4config.cfg

change the entry syslanguage to english

---

### Post by ZDemon on 2007-04-11
That was pretty straight forward

Thanks Rajeev.

---

### Post by an93l on 2007-05-10
i am having the same problem but i can't find the quake4config.cfg or am i looking for the wrong file. if this is obvious i will kick my own ***.

---

### Post by Jaza on 2007-05-10
Open Nautilus and press ctrl+h and go to .quake4 folder (in your home folder) and the config is there.
And to hide those folders again press that ctrl+h ...

---

### Post by an93l on 2007-05-10
i did that and still couldn't find anything? i am going to try reinstalling it

---

### Post by an93l on 2007-05-10
i found it i was looking in the wrong place DOH! my bad

---

### Post by dfm21 on 2008-11-05
So basically a
```

echo "seta sys_lang \"english\"" >> ~/.quake4/q4base/Quake4Config.cfg

```
does the job.

---

