---
title: "Making a screenshot (dual head)"
date: 2005-12-20
forum: Desktop Environments
---

### Post by Ibbelz on 2005-12-20
I want to make a screenshot of my desktop. Works nicely so far (with PrtSc on the keyboard). But the output is only a screenshot of my left monitor, it doesn't make a screenshot of both monitors. Anyone know how I can fix this?

Thanks in advance.

---

### Post by adie273 on 2005-12-20
I had that same problem, 

Quicker just taking a screenshot of both screens and pasting them together into 1 file in GIMP or whatever you prefer. Although I don't have much patience to be honest, and didn't ask anyone if there was a way to fix it.

(Only takes a screenshot of whatever monitor your mouse is sitting in if i remember right)

---

### Post by ranf on 2005-12-20
Install `scrot'. It does this. 
Must be run from a terminal though.

---

### Post by Ibbelz on 2005-12-20
[QUOTE=ranf]Install `scrot'. It does this. 
Must be run from a terminal though.[/QUOTE]

Oh yeah, I installed it with APT and it works like a charm. :) Just type 'scrot -m yourfilename' and it's all done.

Thank you ranf! :)

---

### Post by ranf on 2005-12-20
I just only type 'scrot'. Its file name format is fine for me.

---

### Post by Ibbelz on 2005-12-20
[QUOTE=ranf]I just only type 'scrot'. Its file name format is fine for me.[/QUOTE]

According to the manual -m or --multidisp is necessary for a multi desktop screenshot. Or at least that is wat I understood out of it. :)

```

-m, --multidisp           For multiple heads, grab shot from each and join them together.                          

```

But I just tried it without and that also works niceley. Well, the most important thing is that it works just fine.

---

