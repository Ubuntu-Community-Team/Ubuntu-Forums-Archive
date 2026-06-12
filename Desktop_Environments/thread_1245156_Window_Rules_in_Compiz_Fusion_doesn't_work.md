---
title: "Window Rules in Compiz Fusion doesn't work"
date: 2009-08-20
forum: Desktop Environments
---

### Post by Brausen on 2009-08-20
If I set just one window in "non maximizable windows" field, it works properly. For instante:
```
class=Gthumb
```

But if I set two windows, it stops to work. For instante:
```
class=Gthumb & class=tucan
OR
(class=Gthumb) & class=tucan
OR
(class=Gthumb) & (class=tucan)
```

Someone can help me?
Thanks in advance

---

### Post by mcduck on 2009-08-20
your current rules apply only to windows that are both class "Gthumb" *and* "tucan". That's not going to happen, as long as windows only have one class.

You want the rule to apply to windows that have class "Gthumb" *or* "tucan".

```
class=Gthumb | class=tucan
```

---

### Post by Brausen on 2009-08-20
You're absolutely right
I was thinking that the operators would procede as in bash. Sorry -- and thank you

---

