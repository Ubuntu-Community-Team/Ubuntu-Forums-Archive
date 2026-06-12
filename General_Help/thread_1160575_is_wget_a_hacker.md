---
title: "is wget a hacker?"
date: 2009-05-15
forum: General Help
---

### Post by StOoZ on 2009-05-15
I wonder , when I use the recursive flag (-r) , and give wget a general link , for example : [www.gg.com](www.gg.com)
how does it know that there is a : [www.gg.com/hello](www.gg.com/hello)
[www.gg.com/fff/ff](www.gg.com/fff/ff)
etc??

I mean , how can he find it???

---

### Post by dcstar on 2009-05-15
> **StOoZ said:**
> I wonder , when I use the recursive flag (-r) , and give wget a general link , for example : [www.gg.com](www.gg.com)
how does it know that there is a : [www.gg.com/hello](www.gg.com/hello)
[www.gg.com/fff/ff](www.gg.com/fff/ff)
etc??

I mean , how can he find it???

Web sites can be configured to provide directory contents or not, if they are available then programs like wget can use them.

---

### Post by Bark on 2009-05-16
> **StOoZ said:**
> I wonder , when I use the recursive flag (-r) , and give wget a general link , for example : [www.gg.com](www.gg.com)
how does it know that there is a : [www.gg.com/hello](www.gg.com/hello)
[www.gg.com/fff/ff](www.gg.com/fff/ff)
etc??

I mean , how can he find it???

wget parses the response to find links. It won't find anything which isn't linked from the top page. :KS

---

### Post by StOoZ on 2009-05-16
I see , thanks.

):P

---

