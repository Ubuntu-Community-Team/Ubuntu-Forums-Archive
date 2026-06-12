---
title: "AT (Timed input) File Input"
date: 2015-09-29
forum: Desktop Environments
---

### Post by Geoff_Lane on 2015-09-29
Folks,

I am experimenting with the AT Command but am not sure how the input file works.

If I list more than one wget command in a file does AT issue them one after the other or all together?

Geffers

---

### Post by Lars Noodén on 2015-09-29
One after the other, just like in a normal shell script.  

But keep in mind that at uses /bin/sh (dash) by default instead of /bin/bash, unless you make it do otherwise.

---

