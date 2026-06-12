---
title: "Shell scripting - pause??"
date: 2006-08-03
forum: Desktop Environments
---

### Post by frankerooney on 2006-08-03
Simple question - I've come from a DOS background when it comes to scripting and linux is obviously way better, but I can't for the life of me work out how to just pause a script and wait for the user to press a key! How hard can it be??!

Someone please enlighten me...:confused:

---

### Post by the-linux-guy on 2006-08-03
Use the command "wait" ? ;-)

With kind regards,

Eddy

---

### Post by Thund3rstruck on 2006-08-03
Or use read to pause/wait and accept input from the user

---

### Post by bensexson on 2006-08-03
I also recommend this scripting guide: [http://www.tldp.org/LDP/abs/html/](http://www.tldp.org/LDP/abs/html/)

---

### Post by roostishaw on 2006-08-03
> **Thund3rstruck said:**
> Or use read to pause/wait and accept input from the user
That's what I usually do. I use something like:
```
read -p "Press any key to exit..." anykey
```

---

### Post by frankerooney on 2006-08-05
Thanks for all the suggestions. There's certainly a wealth of knowledge on this forum. Just starting in linux, but the deeper you dig the better it gets! Cheers.

---

