---
title: "scipy / numpy package dependencies in Gutsy"
date: 2008-03-04
forum: Education &amp; Science
---

### Post by WebDrake on 2008-03-04
Hello all,

I'm just wondering why numpy / scipy have python2.4 as a dependency.  Checking the scipy homepage, I don't see any indication this is a requirement.

Can anyone explain?

I'm just rather disinclined to have two versions of Python on my system if there don't need to be ....

Thanks in advance for any comments.

---

### Post by tweedledee on 2008-03-05
I can't tell you why they have 2.4 as the dependency, except perhaps that they didin't get updated, but you can work around it.  Install scipy/numpy normally, then choose "lock version" in Synaptic (or equivalent in other interface) for the two packages.  You should then be able to remove the python2.4 packages, and numpy and scipy should work fine (since 2.5 is the default based on path even if 2.4 is co-installed).

---

### Post by WebDrake on 2008-03-10
Thanks for the suggestion.  I didn't know you could do that! :-)

I learn something every day on these forums...

---

### Post by olivine on 2008-05-06
> **tweedledee said:**
> I can't tell you why they have 2.4 as the dependency, except perhaps that they didin't get updated, but you can work around it.  Install scipy/numpy normally, then choose "lock version" in Synaptic (or equivalent in other interface) for the two packages.  You should then be able to remove the python2.4 packages, and numpy and scipy should work fine (since 2.5 is the default based on path even if 2.4 is co-installed).

I tried to follow these instractions. I installed scipy/numpy, locked numpy, scipy, and matplotlib, and then removed python2.4 and python2.4-minimal. The three packages were uninstalled anyway, and appear as "uninstalled" and "locked" at the same time. Is there something I'm missing here? :(

---

### Post by ItalOz on 2008-05-06
don't know, I have tried both ways
1. compiled installed from sources all the scipy/numpy/etc package.. loooong and painful but succeeded,
2. installed via repositories on another computer and when I launch python I still see on the 2.5 version, so I wonder if this dependency issue is really a problem or not.

---

### Post by olivine on 2008-05-06
Yes, you're right, it doesn't seem to be much of a problem leaving both versions of python installed. I'll leave at that. Thanks.

---

