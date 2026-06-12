---
title: "Problem with nautilus"
date: 2006-09-29
forum: Desktop Environments
---

### Post by Pitbull11188 on 2006-09-29
For some reason when I attempt to open this one folder in my home folder nautilus crashes. It is ONLY this one folder. It contains a pdf that I'd really rather not lose, and due to how it was named I can't copy it anywhere nor can i rename it from the command line. Any ideas on how I can remove this pdf?

---

### Post by thephantomlinguist on 2006-09-29
> **Pitbull11188 said:**
> It contains a pdf that I'd really rather not lose, and due to how it was named I can't copy it anywhere nor can i rename it from the command line.

How was it named? Does it contain illegal characters?

---

### Post by Pitbull11188 on 2006-09-29
"((Demonoid.com))-" minus quotations is in front of it and the terminal tells me it' the (( that causes the problems.

---

### Post by mitch.c on 2006-09-29
> **Pitbull11188 said:**
> "((Demonoid.com))-" minus quotations is in front of it and the terminal tells me it' the (( that causes the problems.

cd to the folder in a terminal, and escape the (( ))- characters like this, or quote it:

WARNING: THIS WILL DELETE THE FILE!!!
```
rm -rf \(\(Demonoid\)\)\-
#OR
rm -rf '\(\(Demonoid\)\)\-'
```

---

### Post by thephantomlinguist on 2006-09-30
> **mitch.c said:**
> 
```
rm -rf \(\(Demonoid\)\)\-
#OR
rm -rf '\(\(Demonoid\)\)\-'
```

I'm sorry I didn't see this earlier. I hope you haven't already done this with the intention of keeping the file. Try

```
mv \(\(Demonoid\)\)\-... demonoid...
```

instead. That'll rename your file (and hopefully make it accessible). rm tends to make things less accessible :( 

Hope this helps!

---

### Post by mitch.c on 2006-09-30
> **thephantomlinguist said:**
> I'm sorry I didn't see this earlier. I hope you haven't already done this with the intention of keeping the file. Try

```
mv \(\(Demonoid\)\)\-... demonoid...
```

instead. That'll rename your file (and hopefully make it accessible). rm tends to make things less accessible :( 

Hope this helps!

I'm glad you pointed that out. Somehow I got it in my mind that we needed to DELETE the file. My apologies.

---

### Post by Pitbull11188 on 2006-09-30
Not a problem I knew not to rm anything. I solved it, but I know there's an easier way. Anyway, My solution was knoppix. Loaded knoppix, found the pdf and then moved it to another folder, and then I deleted the folder giving me the problem. I still don't know WHY nautilus failed, but at least I got my stuff back.

---

