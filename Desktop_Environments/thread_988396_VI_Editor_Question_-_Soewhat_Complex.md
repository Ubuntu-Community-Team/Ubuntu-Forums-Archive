---
title: "VI Editor Question - Soewhat Complex"
date: 2008-11-20
forum: Desktop Environments
---

### Post by ecrossahoo on 2008-11-20
Hi Forum,

I have a "challenge" I have not been able to solve.  I have a file that contains the following

host1.domain.com
beth
albert
vanessa
julie
host2.domain.com
robert
jake
clare
lisa


I would like to add a newline above every line that contains *.domain.com.  So the resulting file would like like:

host1.domain.com
beth
albert
vanessa
julie

host2.domain.com
robert
jake
clare
lisa 


Can someone assist with a little search/replace magic?

](*,)

Thank You.

---

### Post by olejorgen on 2008-11-20
```
:%g/.*domain.com/normal O
```

---

### Post by ecrossahoo on 2008-11-20
Thank you olejorgen.

So "/normal/" will keep in tact the argument in which you intend to mainuplate, then perform the following vi COMMAND-MODE command?

Thanks again for your code.

---

### Post by olejorgen on 2008-11-20
No problem, and yes. (I think you could do something like :%s/(<pattern>)/\n\1 too, but :s and multilines have always caused me headaches)
PS:
```
:help :g 
:help :normal

```

---

