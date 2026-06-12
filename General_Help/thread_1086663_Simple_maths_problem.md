---
title: "Simple maths problem"
date: 2009-03-04
forum: General Help
---

### Post by 5BallJuggler on 2009-03-04
```
phil@phil-netbook:~$ expr  100 \* 11 / 12 
91
phil@phil-netbook:~$ expr  11 / 12 
0
```

expr command does not show decimal values, is there a command that does?

---

### Post by Bachstelze on 2009-03-04
```
firas@nobue ~ % echo "11/12" | bc -l
.91666666666666666666

```

---

### Post by heindsight on 2009-03-04
Bash only does integer arithmetic. If you need something more advanced, you could start up a python interpreter to use as a calculator, or any of the many mathematical programs such as Octave, SciLab or Euler.

If you need floating point arithmetic in shell scripts, then bc (quite easy to use as HymnToLife demonstrated) is probably a good choice.

---

### Post by 5BallJuggler on 2009-03-04
> **HymnToLife said:**
> ```
firas@nobue ~ % echo "11/12" | bc -l
.91666666666666666666

```

Thanks, works a treat.

---

