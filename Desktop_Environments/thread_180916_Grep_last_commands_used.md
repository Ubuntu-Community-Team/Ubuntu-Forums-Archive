---
title: "Grep last commands used"
date: 2006-05-23
forum: Desktop Environments
---

### Post by Nonno Bassotto on 2006-05-23
I'm a Linux noob, so sometimes I do things just by copying and pasting instructions from the forum. Sometimes I also forget which commands I used, so I'm wondering if there's a way to grep words in the last commands used.
I explain better. I can scroll with the up key the last <somebignumber> commands I entered in the terminal. I use this feature also to find some commands I used but I don't remember. This, however, is not practical if a have to scroll one hundred commands. If I remember, say, that the command I'm interested in had to do with the file "myfile", is there a way to speed up the operation?

---

### Post by Sutekh on 2006-05-23
Try using the **history**
```
history | grep <search term>
```
to search for something to with 'myfile'
```
history | grep myfile
```

---

### Post by yota on 2006-05-23
If you press ctrl+r in bash you'll activate the "reverse-i-search" that's exactly what you need (a sort of interactive grep on history).

Really handy!

---

### Post by Sutekh on 2006-05-23
#-o

Thanks for pointing out the obvious solution

---

### Post by Nonno Bassotto on 2006-05-23
Thanks to both!!!:D

---

### Post by yyagol on 2006-05-23
[SIZE="6"][COLOR="Blue"]Hey this is brilliant  
Thanks[/COLOR][/SIZE]

---

