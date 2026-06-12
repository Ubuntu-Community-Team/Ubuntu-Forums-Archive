---
title: "Enemy territory troubles"
date: 2007-04-19
forum: Gaming &amp; Leisure
---

### Post by kane77 on 2007-04-19
I have problem installing. when I try to run the installer I get this: 
```

root@kane-desktop:/home/kane# ./et-linux-2.60.x86.run 
Verifying archive integrity... All good.
Uncompressing Enemy Territory 2.60 Full Install...........
..................................................................................................
............................................................................................
........................................................................................................
.............
./setup.sh: 278: /root/.setup9339: not found
./setup.sh: 289: /root/.setup9339: not found

```

this happens when I run the installer as any user (myself or root) the numbers are different each time (of the .setupXXXX)

I am running amd64 feisty (kernel 2.6.20-15)... Last time I installed (it was on dapper amd64, there were no problems...)

---

### Post by danner on 2007-04-19
I've got exactly same problem. Do:

 apt-get install linux32 

And try again. It usually works (but not for me)

Any other suggestion? :confused:

---

### Post by j0sh0 on 2007-04-20
i had the same trouble and installed libgtk1.2 and that solved it

---

### Post by danner on 2007-04-20
Thanks. I already have them installed :(  I'm trying to download [http://illadvised.com/~jason/ia32-extras-0.1.tar.gz](http://illadvised.com/~jason/ia32-extras-0.1.tar.gz) as suggested somewhere, but the URL is not working :shock:

---

### Post by lakersforce on 2007-04-21
I found the solution! Look here: [http://ubuntuforums.org/showthread.php?t=416871](http://ubuntuforums.org/showthread.php?t=416871)

---

### Post by kane77 on 2007-04-23
> **lakersforce said:**
> I found the solution! Look here: [http://ubuntuforums.org/showthread.php?t=416871](http://ubuntuforums.org/showthread.php?t=416871)

yes! this works really well! Thank you!

---

### Post by danner on 2007-04-25
Same to me :lolflag:  

Now I have to fix some problem with framerate :confused: Maybe I'm using wrong OpenGL lib files... Something to work on ;)

---

