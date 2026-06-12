---
title: "lyx impoverished, less classes, no tex2lyx"
date: 2007-07-06
forum: Education &amp; Science
---

### Post by mommebu on 2007-07-06
In the feisty install the lyx packages seem to have been strongly impoverished for some reason, a lot of document classes like the koma-script classes, that were included earlier, are not availlable anymor and also the latex to lyx converter tex2lyx has disapppeared. A.body knows where they have gone, why they were taken away and how one could recover the missing parts?

thanks,
momme

---

### Post by kleeman on 2007-07-06
That's odd but Ubuntu packages website shows tex2lyx as part of the lyx package on feisty. What does

ls -al /usr/bin/tex2lyx 

show?

---

### Post by mommebu on 2007-07-16
ls: /usr/bin/tex2lyx: No such file or directory

...as I said tex2lyx doesn't exist on my system after installation of lyx (lyx-qt).

---

### Post by kleeman on 2007-07-16
As I said it is in the lyx package. Fire up synaptic and search for lyx. You will see the lyx package along with the lyx-qt package. If the lyx package is not installed then install it. If it IS installed reinstall it ( package----------> mark for reinstallation  then apply).

---

### Post by mommebu on 2007-07-16
OK, now I got it. sorry bout the confusion, but from the descriptions in synaptic I understood, that the base package was lyx-common and the others were flavours. my fault...

---

