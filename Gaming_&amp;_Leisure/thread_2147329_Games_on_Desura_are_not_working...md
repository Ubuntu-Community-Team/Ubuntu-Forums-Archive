---
title: "Games on Desura are not working.."
date: 2013-05-21
forum: Gaming &amp; Leisure
---

### Post by ViliX64 on 2013-05-21
Hi, I started using Desura and noticed, that I can play about 50% of the games I download.
I am talking about Stunt Rally (6.5) and Warzone 2100 (9.3). When I choose Stunt Rally and choose "Play", nothing happens. And when I try to launch Warzone 2100, it does not do anything..
I have Ubuntu 13.04 and Intel HD 2000.

Thank you for any help..

---

### Post by King Dude on 2013-05-21
Intel video cards are a real pain.

---

### Post by ViliX64 on 2013-05-21
I know (from my experience), but there must be a way..

---

### Post by King Dude on 2013-05-21
When did the problem start to occur? When you upgraded to 13.04, or did it just stop working one day?

---

### Post by ViliX64 on 2013-05-22
Well, I have started using Desura now, on 13.04.. I did not tried to play games on 12.10 or 12.04 (I have been using..)

---

### Post by oldrocker99 on 2013-05-22
Try this: Open a termina, and navigate to your ~/desura/common/stunt-rally folder. Enter ./name-of-executable, then post the output. This is the best way to find out why a program doesn't run.

---

### Post by ViliX64 on 2013-05-22
```

./desura_launch_Play.sh 
/home/vilix/desura/common/stunt-rally/bin/stuntrally_x86_64: error while loading shared libraries: libopenjpeg.so.2: cannot open shared object file: No such file or directory

```
I am totally noob.. I don't know what that means..

---

### Post by ViliX64 on 2013-05-22
Wait for it.. I have installed libopenjpeg and it seems to work!

---

### Post by ViliX64 on 2013-05-22
But I am having more problems with Puzzle Moppet.. The error code is here:
```

/desura/common/puzzle-moppet$ ./desura_launch_Play.sh
./PuzzleGame: error while loading shared libraries: libGL.so.1: cannot open shared object file: No such file or directory

```

---

