---
title: "ATI trouble with new card."
date: 2008-03-04
forum: Desktop Effects &amp; Customization
---

### Post by Cylant on 2008-03-04
Hey everyone. I am using a x3870 graphics card. I tried the steps for installing the drivers for older cards just to see if i got lucky.

My computer is working, but i cant enable any custom desktop features. I got the restricted driver manager working, however it doesn't see my card.

Did i screw myself by buying a sweet card or is there hope for me yet. Thanks in advance.

---

### Post by Melcar on 2008-03-04
The drivers are working right?  You have direct rendering?  If the answer is yes to both questions, the problem is in the /usr/bin/compiz file.  You have to add fglrx to the whitelisted drivers for desktop effects to work.

---

