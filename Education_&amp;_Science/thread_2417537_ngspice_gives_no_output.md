---
title: "ngspice gives no output"
date: 2019-04-24
forum: Education &amp; Science
---

### Post by johnsmith12345678 on 2019-04-24
Hello,

when i run the following circuit via ngspice(Lubuntu 18.04),

```

circuit
V 0 1  DC 10
R 0 1 5
.end

```
it outputs this:
```

Circuit: circuit


ngspice 1 -> 

```
"print all" leads to this:
```

Circuit: circuit


ngspice 1 -> print all
false = 0.000000e+00
true = 1.000000e+00
boltz = 1.380620e-23
c = 2.997925e+08
e = 2.718282e+00
echarge = 1.602190e-19
i = 0.000000e+00,1.000000e+00
kelvin = -2.73150e+02
no = 0.000000e+00
pi = 3.141593e+00
planck = 6.626200e-34
yes = 1.000000e+00

```
Why is there no output?

Thanks in advance

---

