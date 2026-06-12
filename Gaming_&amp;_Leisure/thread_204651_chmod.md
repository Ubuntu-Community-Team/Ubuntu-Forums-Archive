---
title: "chmod"
date: 2006-06-27
forum: Gaming &amp; Leisure
---

### Post by AngryKidJoe on 2006-06-27
[quote="Eternal Lands HomePage"]chmod to 775[/quote]
I don't recall ever seeing any number variables in chmod. I've looked at some tutorials and didn't see anything. Did I skip over something?

---

### Post by digimars on 2006-06-27
I did this last night, just do 
```

chmod 775 el.x86.linux.bin

```

And it will work.  To run it go to the game's directory and do 
```

./el.x86.linux.bin

```

That should get you up and running.

---

### Post by keithjr on 2006-06-27
[QUOTE=AngryKidJoe]I don't recall ever seeing any number variables in chmod. I've looked at some tutorials and didn't see anything. Did I skip over something?[/QUOTE]


The number variables are a triple of octal numbers (base-8 number system), which make a really nice system.  They allow for any combination of read,write, and/or execute to be applied to owner, group, and other users.  Actually, there can even be four digits, in which case the first digit applies to the user who's doing the change-moding, if I'm not wrong.  The number used is the sum of the permissions you want to enable (1 for execute, 2 for read, 4 for write)

[this is a good page for reference.]("http://www.ss64.com/bash/chmod.html")  This is important knowledge for any linux user.  The little interactive box should teach you what you need to know

---

### Post by digimars on 2006-06-27
That's a handy page!  Thank you for that!

---

### Post by handy on 2006-06-28
[QUOTE=keithjr]The number variables are a triple of octal numbers (base-8 number system), which make a really nice system.  They allow for any combination of read,write, and/or execute to be applied to owner, group, and other users.  Actually, there can even be four digits, in which case the first digit applies to the user who's doing the change-moding, if I'm not wrong.  The number used is the sum of the permissions you want to enable (1 for execute, 2 for read, 4 for write)

[this is a good page for reference.]("http://www.ss64.com/bash/chmod.html")  This is important knowledge for any linux user.  The little interactive box should teach you what you need to know[/QUOTE]


Superb Link! :KS

---

### Post by keithjr on 2006-06-29
[QUOTE=handy]Superb Link! :KS[/QUOTE]



... Google + "chmod octal" ...

---

