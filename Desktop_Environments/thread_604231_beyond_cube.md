---
title: "beyond cube"
date: 2007-11-05
forum: Desktop Environments
---

### Post by scuba_suit on 2007-11-05
okay i've seen what people have done with their cubes on the youtube, but how far can someone really take the concept? what else can be done on the desktop? are there plugins that take it further than what you can do on the ccsm?

---

### Post by Tyke91 on 2007-11-05
well... i've turned mine into a heptagon instead of a cube... does that count?

also, you can use a tool to make your mouse pointer draw any colored fire on the screen (which is good for pointing things out in screenies) I know there is a less flashy "marker" version of this as well

I think project looking glass has a neat concept with their "free floating" windows in a 3D desktop environment (kinda like walking around a park with random windows everywhere)

what I think would be cool (i don't know if this would actually work at all) is if we placed all the desktop cubes there are into a sort of giant 3D world where you could zoom away from your own cube and see (and possibly control with a password) someone elses cube.  kind of like the an internet browser, except in 3D              :0

---

### Post by santiagoward2000 on 2007-11-05
Have you seen Project Looking-Glass? It looks great. Here's a video:
[http://www.youtube.com/watch?v=JXv8VlpoK_g]("http://www.youtube.com/watch?v=JXv8VlpoK_g")

Although still prefer my cube...

---

### Post by BennBuntu on 2007-11-05
was sorta surprised by the audience reaction to that sun thingy. Guess I forget how few people know there are alternatives to Micro$oft.

---

### Post by jimerickso on 2007-11-06
> **santiagoward2000 said:**
> Have you seen Project Looking-Glass? It looks great. Here's a video:
[http://www.youtube.com/watch?v=JXv8VlpoK_g]("http://www.youtube.com/watch?v=JXv8VlpoK_g")

Although still prefer my cube...
if you compile from git (master-noxcb) you can use the freewins plugin which allows you to rotate windows in 3 dimensions like you can with looking glass.

---

### Post by santiagoward2000 on 2007-11-06
> **jimerickso said:**
> if you compile from git (master-noxcb) you can use the freewins plugin which allows you to rotate windows in 3 dimensions like you can with looking glass.

Doesn't Gusty have problems when compiling Compiz-Fusion from git? At least that's what I read...

---

### Post by jimerickso on 2007-11-06
i just use the makefusion8 script on this page

[http://telperion.wordpress.com/2007/10/27/fusion-nuovo-script-per-compilazione/](http://telperion.wordpress.com/2007/10/27/fusion-nuovo-script-per-compilazione/)

its in italian but it translates ok with google translate. the script worked like a charm for me. you will have to fill in certain values in the script to make it work but it is worth the effort.  make sure to remove the old compiz-fusion before running the script. good luck!

---

### Post by shafin on 2008-01-02
There is a version of the freewins that works with gutsy's compiz fusion.

Extract the archive,go tho the folder in terminal and
```
make
```
```
sudo make install
```

---

### Post by adityakavoor on 2008-01-02
I get this error 

```

sudo make install

[sudo] password for aditya:

bcop'ing  : build/freewins.xml -> build/freewins_options.h/bin/sh: 

--header=build/freewins_options.h: not found

make: *** [build/freewins_options.h] Error 127


```

what is the problem ?

---

### Post by shafin on 2008-01-04
> **adityakavoor said:**
> I get this error 

```

sudo make install

[sudo] password for aditya:

bcop'ing  : build/freewins.xml -> build/freewins_options.h/bin/sh: 

--header=build/freewins_options.h: not found

make: *** [build/freewins_options.h] Error 127


```what is the problem ?
evidently there is an error in the source,check out this post for the solution:
[http://forum.compiz-fusion.org/showpost.php?p=44218&postcount=14](http://forum.compiz-fusion.org/showpost.php?p=44218&postcount=14)

---

### Post by jryprt on 2008-01-04
> **shafin said:**
> evidently there is an error in the source,check out this post for the solution:
[http://forum.compiz-fusion.org/showpost.php?p=44218&postcount=14](http://forum.compiz-fusion.org/showpost.php?p=44218&postcount=14)

This works great , freewins gets renamed in compiz manager to 
Freely transform windows

---

### Post by adityakavoor on 2008-01-13
> **shafin said:**
> evidently there is an error in the source,check out this post for the solution:
[http://forum.compiz-fusion.org/showpost.php?p=44218&postcount=14](http://forum.compiz-fusion.org/showpost.php?p=44218&postcount=14)

problem still persists :( :( :(

---

### Post by Romanus81 on 2008-01-13
Try make install without sudo or root. It worked for me once.

---

