---
title: "File Shredder"
date: 2009-02-03
forum: General Help
---

### Post by MarkPolo on 2009-02-03
Anybody know about a file shredding utility for Ubuntu?  I'm uncomfortable just tossing sensitive documents into the trash.

---

### Post by abn91c on 2009-02-03
try Kleansweep, its in the Repos

---

### Post by MarkPolo on 2009-02-03
No.  Kleensweep is for deleting seldom-used files, not for deleting beyond recovery any sensitive files.

---

### Post by adamlau on 2009-02-03
shred is a native tool:

```
shred -fuz /path/to/document
```

---

### Post by mc4man on 2009-02-03
Not sure about kubuntu but there is a built-in shred utility in ubuntu. (can be made into a right click action but only in nautilus I believe.

There's also secure-delete and probably others.

Many will say 'shred' isn't 'good' enough though I'm sure 99.99% of those you do couldn't recover a shredded file.

---

### Post by adamlau on 2009-02-04
shred can also be used within a Thunar UCA as such (using zenity):

```
zenity --question;if [$? = 0];then shred -fuz %F;fi
```

---

### Post by Tulsapoke on 2009-02-15
I missed the old KGPG desktop shredder when they dropped it.  I finally figured out that I could put the command line into an icon and have the basic functionality back.

create a launcher
put   shred -f -u -v -z %M   into the command section
name it shredder and give it a cool icon that clearly denotes the danger of it and you are done.  Now you can just drop files onto the shredder icon and they will be securely deleted.  

Only thing I wish it did was give me a confirmation dialog since this seems like it could be used accidentally.

---

