---
title: "Noobquestion: Copying"
date: 2009-03-03
forum: General Help
---

### Post by Kerel on 2009-03-03
```
cp /windows/Users/Kerel/Documents/Rips/test /media/KerelHD/test
```

I also did a 

 ```
mv /windows/Users/Kerel/Documents/Rips/test /media/KerelHD/test
```

And I cannot find the files, what am I doing wrong? 
(My ext hd is KerelHD, duh)

Thx in advance

---

### Post by dargaud on 2009-03-03
Assuming test is a file and not a directory,
```
cp /windows/Users/Kerel/Documents/Rips/test /media/KerelHD/
```
is enough. Add the -v option to see what's going on. Do ```
ls -alF /media/KerelHD/
``` show anything ?

---

### Post by Kerel on 2009-03-03
> **dargaud said:**
> Assuming test is a file and not a directory,

 Oops, it's a directory with test.wav in it..
Nothing yet.

Tried this, 
```

cp -v ~/Documents/aap /media/KerelHD/aap
```

Result

```

cp: omitting directory `/home/kerel/Documents/aap'
```

Real result

can't see ****.

---

### Post by Vaphell on 2009-03-03
-r for recursion?

cp -r should recreate directory structure

---

### Post by Kerel on 2009-03-03
> **Vaphell said:**
> -r for recursion?

cp -r should recreate directory structure

That was the problem ! Thx for the help.

---

### Post by dhughes on 2009-03-03
That's weird, I figured you needed the -r for cp but I thought ```
mv /windows/Users/Kerel/Documents/Rips/test /media/KerelHD/test
``` should have worked since -r isn't an option with the mv command.

---

