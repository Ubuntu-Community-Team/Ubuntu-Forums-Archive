---
title: "[SOLVED] rm: cannot remove &amp;lt;filename&amp;gt; Input/output error"
date: 2008-12-27
forum: General Help
---

### Post by mrmaster on 2008-12-27
Hi,

I have a file on my external drive which I can't delete. I keep getting the error message in my title. I tried to look online how to solve the problem but the explanations seems confusing so i'm hoping someone here can help.

I am using ubuntu 8.10 with  2.6.27-9-generic kernel. And i'm trying to delete a file not a directory. 

Thanks

---

### Post by ravindukelum on 2008-12-27
try as root

<sudo rm -r filename>

---

### Post by jerome1232 on 2008-12-27
Well making rm recursive isn't going to do much for a file. I'd suggest the -f flag, it forces the operation.

```
rm -f *filename*
### and of course if you don't have permission to delete the file
sudo rm -f *filename*
```

---

### Post by mrmaster on 2008-12-28
Hi,

Basically what happened was that the data was corrupt and thats why i couldn't delete it. Well before i received both of your messaged i decided to do a check disk(windows xp) and they have fix bad sectors option which solved my problem. 

Thank you for your advices though

---

### Post by dcstar on 2008-12-28
> **mrmaster said:**
> Hi,

Basically what happened was that the data was corrupt and thats why i couldn't delete it. Well before i received both of your messaged i decided to do a check disk(windows xp) and they have fix bad sectors option which solved my problem. 

Thank you for your advices though

Which is why you will now mark the thread as solved, right?

---

### Post by mrmaster on 2008-12-28
> **dcstar said:**
> Which is why you will now mark the thread as solved, right?

Yes sir and thanks for the reminder :)

---

### Post by murphyb on 2009-10-29
If he went to Windows to solve this problem is it really solved?  I'm having the same problem but I would prefer not to correct through Windows.

---

### Post by dea on 2009-11-04
yeah, same from me - is running scandisk in XP the only way to solve this?? What's with you, linux people, am I to install XP on my machine? :D

---

