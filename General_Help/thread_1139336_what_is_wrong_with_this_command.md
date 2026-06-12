---
title: "what is wrong with this command"
date: 2009-04-26
forum: General Help
---

### Post by Cacaco on 2009-04-26
xrandr -display --output rotate inverted

I'm using a Dell Pentium 3, what I'd like to to is to invert the display Upsidedow.

Thanks

---

### Post by 987poiuytrewq on 2009-04-27
I think you want

```
xrandr -o inverted
```

but typing 

```
man xrandr
```

should give you a full list of options to play with.

---

