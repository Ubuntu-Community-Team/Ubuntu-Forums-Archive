---
title: "Prompt mangled by Bash tab completion"
date: 2009-05-31
forum: Desktop Environments
---

### Post by purecharger on 2009-05-31
Hi-

My custom prompt gets mangled when I tab-complete filenames. I've attached two screenshots, pretab.jpg and posttab.jpg, showing the prompt prior to and after tab completion, respectively.

Version info:
Ubuntu 9.04
Gnome Terminal 2.26.0
GNU bash, version 3.2.48(1)-release (i486-pc-linux-gnu)

I used to have this same setup on my machine at work and it did not have the same problem. I dont work at the same job anymore, so I can't investigate why it works there and not on my home machine.

Any clues?

Thanks!

---

### Post by asmoore82 on 2009-06-01
could you post your 'PS1' ?
```
echo "$PS1"
```

---

### Post by purecharger on 2009-06-01
> **asmoore82 said:**
> could you post your 'PS1' ?
```
echo "$PS1"
```

(rnideffer@rnideffer-lin)(11:42pm)-
($:~)- echo "$PS1"
\[\033[1;30m\]&#65533;\[\033[0;36m\]&#65533;\[\033[1;36m\](\[\033[0;36m\]\u@\h\[\033[1;36m\])\[\033[0;36m\]&#65533;\[\033[1;36m\](\[\033[0;36m\]$(date +%I:%M%P)\[\033[1;36m\])\[\033[0;36m\]&#65533;\[\033[1;30m\]-\[\033[0m\]\n\[\033[1;30m\]&#65533;\[\033[0;36m\]&#65533;\[\033[1;36m\](\[\033[0;36m\]$\[\033[1;30m\]:\[\033[0;36m\]\w\[\033[1;36m\])\[\033[0;36m\]&#65533;\[\033[1;30m\]-\[\033[0m\] 

heres the hexdump for the unprintable chars:

```

0000000   \   [   \   0   3   3   [   1   ;   3   0   m   \   ] 332   \
0000010   [   \   0   3   3   [   0   ;   3   6   m   \   ] 304   \   [
0000020   \   0   3   3   [   1   ;   3   6   m   \   ]   (   \   [   \
0000030   0   3   3   [   0   ;   3   6   m   \   ]   \   u   @   \   h
0000040   \   [   \   0   3   3   [   1   ;   3   6   m   \   ]   )   \
0000050   [   \   0   3   3   [   0   ;   3   6   m   \   ] 304   \   [
0000060   \   0   3   3   [   1   ;   3   6   m   \   ]   (   \   [   \
0000070   0   3   3   [   0   ;   3   6   m   \   ]   $   (   d   a   t
0000080   e       +   %   I   :   %   M   %   P   )   \   [   \   0   3
0000090   3   [   1   ;   3   6   m   \   ]   )   \   [   \   0   3   3
00000a0   [   0   ;   3   6   m   \   ] 304   \   [   \   0   3   3   [
00000b0   1   ;   3   0   m   \   ]   -   \   [   \   0   3   3   [   0
00000c0   m   \   ]   \   n   \   [   \   0   3   3   [   1   ;   3   0
00000d0   m   \   ] 300   \   [   \   0   3   3   [   0   ;   3   6   m
00000e0   \   ] 304   \   [   \   0   3   3   [   1   ;   3   6   m   \
00000f0   ]   (   \   [   \   0   3   3   [   0   ;   3   6   m   \   ]
0000100   $   \   [   \   0   3   3   [   1   ;   3   0   m   \   ]   :
0000110   \   [   \   0   3   3   [   0   ;   3   6   m   \   ]   \   w
0000120   \   [   \   0   3   3   [   1   ;   3   6   m   \   ]   )   \
0000130   [   \   0   3   3   [   0   ;   3   6   m   \   ] 304   \   [
0000140   \   0   3   3   [   1   ;   3   0   m   \   ]   -   \   [   \
0000150   0   3   3   [   0   m   \   ]      \n                        
000015a

```

---

### Post by purecharger on 2009-06-16
Any ideas..?

---

### Post by purecharger on 2009-08-17
Bump.

Is there a more specific support forum for the Terminal application?

---

### Post by asmoore82 on 2009-08-17
I don't know what the purpose of the unprintable characters is;
but I've simplified your PS1 down to this:
```
PS1='\[\033[1;36m\](\[\033[0;36m\]\u@\h\[\033[1;36m\])(\[\033[0;36m\]$(date +%I:%M%P)\[\033[1;36m\])\[\033[1;30m\]-\n\[\033[1;36m\](\$\[\033[1;30m\]:\[\033[0;36m\]\w\[\033[1;36m\])\[\033[1;30m\]-\[\033[0m\] '
```
It seems effectively identical and is not causing me any trouble with tabbing.

---

### Post by purecharger on 2009-08-17
Awesome, that did it. Thank you!

---

