---
title: "Inverting content of a file"
date: 2009-03-26
forum: General Help
---

### Post by perhaugaard on 2009-03-26
Dear Ubuntu Users,

A quick newbe question :confused:

I have generated a file with a list of data which I would like to invert. Is there an easy way to do this?

Any input is appreciated.


/Per

---

### Post by dandnsmith on 2009-03-26
I suppose you mean you want the list in reverse order, rather than any other sort of inversion (such as 0->1, 1->0 for binary)?

I'm sure there is a way, but can't get my mind past alpha or numeric sorts at this moment.

---

### Post by kaibob on 2009-03-26
> **perhaugaard said:**
> ...I have generated a file with a list of data which I would like to invert. Is there an easy way to do this? Any input is appreciated.

If by invert you mean list in reverse order, the following will do what you want:

```
tac oldfile > newfile
```

[http://linuxcommand.org/man_pages/tac1.html](http://linuxcommand.org/man_pages/tac1.html)

---

### Post by perhaugaard on 2009-03-26
Thanks, the tec-command is just what I was looking for.

---

### Post by dandnsmith on 2009-03-26
Thanks, kaibob, the tac is a new one on me, and sounds worth remembering.

---

