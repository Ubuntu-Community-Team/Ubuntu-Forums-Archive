---
title: "d1x-rebirth install problems."
date: 2006-12-29
forum: Gaming &amp; Leisure
---

### Post by Larsen on 2006-12-29
I have just compiled and installed d1x rebirth.
I have installed the SDL library with no probs and the Physfs library with no probs.
My distro is 6.06LTS

When I try to run it from the menu I get (drumroll)nothing.
When I run it from terminal I get bash: command not found even though I'm looking at it. 
(Yes I have double checked case and spelling)
Permissions are set to basically everything for everyone. 
When I run it with a full directory tree it executes and tells me that it cant find some files see insert.
```

len@tokyo-3:/usr/local$ cd games
len@tokyo-3:/usr/local/games$ ls
d1x-rebirth-gl
len@tokyo-3:/usr/local/games$ d1x-rebirth-gl
bash: d1x-rebirth-gl: command not found
len@tokyo-3:/usr/local/games$ d1x-rebirth-gl
bash: d1x-rebirth-gl: command not found
len@tokyo-3:/usr/local/games$ ls
d1x-rebirth-gl
len@tokyo-3:/usr/local/games$ /usr/local/games/d1x-rebirth-gl

Error: Cannot open file DESCENT.TEX or DESCENT.TXB

Error: Cannot open file DESCENT.TEX or DESCENT.TXB

```

I've tried copying the HI-res fonts and the hi-res breifings to the data directory.
Data directory is /usr/local/share/games/d1x-rebirth/
Binary is in /usr/local/games/

No effect. Anyone got any ideas?
My original descent files have no *.txb or *.tex files in them and it runs fine in dosbox but slooooowwwwwwlllllly'y'y'y'y'y'y even with frameskip 4.

I'm guessing I'm not the first person to have tried installing this so I'm hoping someone knows the answer. :confused: 

Install was with 
sudo scons followed by 
sudo scons -install

Thanks in advance for any help.

Larsen.

---

### Post by Larsen on 2006-12-29
Solved:

Rename DESCENT.HOG and DESCENT.PIG to descent.hog and descent.pig

It seems it borks on capitals.

Question the second.
What framerates are normal with descent on linux.

Larsen.

---

