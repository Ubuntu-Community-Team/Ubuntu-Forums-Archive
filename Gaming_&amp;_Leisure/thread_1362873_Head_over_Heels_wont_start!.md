---
title: "Head over Heels wont start!"
date: 2009-12-23
forum: Gaming &amp; Leisure
---

### Post by Rytron on 2009-12-23
Hi.
I installed Head over Heels.

It wont start. Here is the terminal output.

```
$ hoh
/usr/local/bin/hoh: line 4: /usr/local/share/games/HoH/HoH: No such file or directory
/usr/local/bin/hoh: line 4: exec: /usr/local/share/games/HoH/HoH: cannot execute: No such file or directory
```

How do I remedy this?

Thanks.

---

### Post by qalimas on 2009-12-23
Looks like there is nothing where it thinks it is.

To confirm can you post the output of `ls /usr/local/share/games/` and `ls /usr/local/share/games/HoH`?

---

### Post by Qola on 2009-12-23
[This](http://en.wikipedia.org/wiki/Head_Over_Heels_%28video_game%29)?

---

### Post by Rytron on 2009-12-24
> **Qola said:**
> [This](http://en.wikipedia.org/wiki/Head_Over_Heels_%28video_game%29)?

Yes. :)

---

### Post by Rytron on 2009-12-24
> **qalimas said:**
> Looks like there is nothing where it thinks it is.

To confirm can you post the output of `ls /usr/local/share/games/` and `ls /usr/local/share/games/HoH`?

```
:~$ ls /usr/local/share/games/
HoH  sdlmame

:~$ ls /usr/local/share/games/HoH
HoHOriginal.dat  HoH.txt  runtime  Sound
```

---

### Post by aki.km on 2009-12-24
> **Rytron said:**
> ```
:~$ ls /usr/local/share/games/
HoH  sdlmame

:~$ ls /usr/local/share/games/HoH
HoHOriginal.dat  HoH.txt  runtime  Sound
```
Even I got the solution of my problem too. 
Thanks for the post

---

### Post by Qola on 2009-12-24
> **Rytron said:**
> Yes. :)

Would something that old even run on linux?

---

### Post by hikaricore on 2009-12-24
It ran a couple years ago, I remember playing the damn thing.

---

### Post by Rytron on 2009-12-24
> **aki.km said:**
> Even I got the solution of my problem too. 
Thanks for the post

What was the solution?

---

### Post by Rytron on 2009-12-24
> **Qola said:**
> Would something that old even run on linux?

Absolutely. I did get it running easily in a previous version of Ubuntu. Get it [here]("http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/Puzzle/Head-Over-Heels-4550.shtml").

---

### Post by hikaricore on 2009-12-24
Just tested it again and it works.

I'm assuming you downloaded it from here?
[http://retrospec.sgn.net/games/hoh/downloads.html](http://retrospec.sgn.net/games/hoh/downloads.html)

You'll need to extract it.
Then run: **sudo ./install.sh** from the path.
Hit the enter key boom done.

Type: **hoh**

Not checked for menu entries but they should work if it has them.

---

### Post by Rytron on 2009-12-24
> **hikaricore said:**
> Just tested it again and it works.

I'm assuming you downloaded it from here?
[http://retrospec.sgn.net/games/hoh/downloads.html](http://retrospec.sgn.net/games/hoh/downloads.html)

You'll need to extract it.
Then run: **sudo ./install.sh** from the path.
Hit the enter key boom done.

Type: **hoh**

Not checked for menu entries but they should work if it has them.

I got it from [here]("http://linux.softpedia.com/get/GAMES-ENTERTAINMENT/Puzzle/Head-Over-Heels-4550.shtml").

I just downloaded the one from [here]("http://retrospec.sgn.net/games/hoh/downloads.html").
It works perfectly. :P

Strange thing is that I ran sudo **./install.sh** for the old one also. Aswell as that both download links give the same version (1.01).

Cheers hikaricore.

---

