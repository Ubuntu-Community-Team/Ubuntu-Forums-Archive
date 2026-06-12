---
title: "good racing games for ubuntu"
date: 2007-09-19
forum: Gaming &amp; Leisure
---

### Post by markp1989 on 2007-09-19
does any one know a good racing game that is similar to burnout ?

---

### Post by Perfect Storm on 2007-09-19
vdrift perhaps?

[http://vdrift.net/](http://vdrift.net/)

Torsc

[http://torcs.sourceforge.net/](http://torcs.sourceforge.net/)

Trigger

[http://sourceforge.net/project/showfiles.php?group_id=157028](http://sourceforge.net/project/showfiles.php?group_id=157028)

---

### Post by Steveway on 2007-09-19
How about tuxcart?

---

### Post by Sockerdrickan on 2007-09-19
If you use WINE then Flatout and Flatout 2 works 100% ;)

---

### Post by hobieone on 2007-09-19
need for speed most wanted works well under wine also :KS

---

### Post by RomeReactor on 2007-09-19
Although it's more of a driving sim than a true racing game, maybe you'll like [Racer]("http://racer.nl/").

[Here]("http://racer.nl/images/screenshot0101.jpg") [are]("http://racer.nl/images/screenshot020.jpg") [a]("http://racer.nl/images/screenshot013.jpg") [few]("http://racer.nl/images/c4.jpg") [screenshots]("http://racer.nl/images/gt500_lg.jpg").

You can get it [here]("http://racer.nl/dl_beta_linux.htm").

---

### Post by Sockerdrickan on 2007-09-20
I tried that it's... weird

---

### Post by markp1989 on 2007-09-20
> **RomeReactor said:**
> Although it's more of a driving sim than a true racing game, maybe you'll like [Racer]("http://racer.nl/").

[Here]("http://racer.nl/images/screenshot0101.jpg") [are]("http://racer.nl/images/screenshot020.jpg") [a]("http://racer.nl/images/screenshot013.jpg") [few]("http://racer.nl/images/c4.jpg") [screenshots]("http://racer.nl/images/gt500_lg.jpg").

You can get it [here]("http://racer.nl/dl_beta_linux.htm").

I installed this game ,b ut i cant run it, when i tried running it from the terminal i get  a error 

"mark@markspc:~$ '/home/mark/racer/racer' 
./bin/racer: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory"

---

### Post by Perfect Storm on 2007-09-20
> **markp1989 said:**
> I installed this game ,b ut i cant run it, when i tried running it from the terminal i get  a error 

"mark@markspc:~$ '/home/mark/racer/racer' 
./bin/racer: error while loading shared libraries: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory"

Do;

```
sudo aptitude install libstdc++2.10-glibc2.2
```

---

### Post by markp1989 on 2007-09-20
> **Artificial Intelligence said:**
> Do;

```
sudo aptitude install libstdc++2.10-glibc2.2
```

Thanks that worked well, is there  a way i can use my controler with this game instead of the mouse?

---

### Post by Perfect Storm on 2007-09-20
Sorry, can't help you there.

---

### Post by markp1989 on 2007-09-20
> **hobieone said:**
> need for speed most wanted works well under wine also :KS

I tried installing NFS most wanted with wine, but i get an error message about direct x not being installed?

---

