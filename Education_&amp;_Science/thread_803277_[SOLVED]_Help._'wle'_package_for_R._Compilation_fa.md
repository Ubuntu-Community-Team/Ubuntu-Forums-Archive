---
title: "[SOLVED] Help. 'wle' package for R. Compilation failed."
date: 2008-05-22
forum: Education &amp; Science
---

### Post by desper on 2008-05-22
Dear all,

I met an compilation error when trying to install 'wle' package for the stepwise function in R. With the command 'install.packages("wle")'

it complains that 
```
 
/usr/bin/ld: cannot find -lblas
collect2: ld returned 1 exit status
make: *** [wle.so] Error 1

```

Please help if you have some thoughts on the issue.


Best Regards,

desper

---

### Post by desper on 2008-05-22
Solved by installing refblas3-dev. 

Thanks to [COLOR="Blue"]po0f@ubuntuforums[/COLOR]
[http://ubuntuforums.org/showthread.php?t=362524](http://ubuntuforums.org/showthread.php?t=362524)

---

### Post by tchu on 2008-07-15
I needed to install both

gfortran and
refblas3-dev

from Synaptic Package Manager before R's wle package to get it to work.

---

