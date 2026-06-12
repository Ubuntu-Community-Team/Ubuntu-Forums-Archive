---
title: "Stepmania: Access Denied"
date: 2009-01-02
forum: Gaming &amp; Leisure
---

### Post by wall0645 on 2009-01-02
I just installed Stepmania off the binary file given on the website, though when I try to run it, it says
```
bash: /usr/games/StepMania-3.9/stepmania: Permission denied

```

I also cannot view the folder's contents outside of the terminal (i.e., I can't "look" at it graphically).

How do I modify the folder permissions so that I can run the program?

Thanks!

---

### Post by F!N@LC0MP0S!T3 on 2009-01-02
Did you tried using Chmod + your folder?

btw,did your tried with root?

---

### Post by rsay on 2009-01-02
```
sudo chmod o+x /usr/games/StepMania-3.9/stepmania
sudo chmod o+r /usr/games/StepMania-3.9
```
This should make the command executable by anyone and the folder readable by anyone.

You would have to change ownership (chown) if you want to limit the execution to a certain user or group. For example:
```
sudo chown root:games /usr/games/StepMania-3.9/stepmania
sudo chmod g+x /usr/games/StepMania-3.9/stepmania
```
This would make the program executable by any member of the games group.


In general, you don't want to run programs as root.

---

### Post by albinootje on 2009-01-02
> **wall0645 said:**
> 
I also cannot view the folder's contents outside of the terminal (i.e., I can't "look" at it graphically).

```

gksu nautilus

```
Be careful with this however, only use when it's really needed!

To make everyone able to cd into that directory :
```

sudo chmod 755 /usr/games/StepMania-3.9/

```

---

### Post by wall0645 on 2009-01-02
thanks all! with your guidance I was able to do it :)

---

