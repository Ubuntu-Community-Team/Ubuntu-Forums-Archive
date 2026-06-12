---
title: "A fairly basic sed / regex question"
date: 2009-04-28
forum: General Help
---

### Post by lumix on 2009-04-28
If I have

> 
one
break
two
three
break2
four
break3
five


and I'd like to replace everything between the "break" and "break3" strings with "xxx", can I do this with sed?  a simple "sed s/break.*break3/xxx/g doesn't seem to do this, presumably because it starts over at each new line.

---

### Post by sdennie on 2009-04-28
Try:

```

sed -e '/break/,/break3/s/.*/xxx/'

```

I think it's a little more complicated if you don't want the "break" statements converted.

---

