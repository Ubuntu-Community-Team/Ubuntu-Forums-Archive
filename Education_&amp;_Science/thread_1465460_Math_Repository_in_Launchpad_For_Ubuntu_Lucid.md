---
title: "Math Repository in Launchpad For Ubuntu Lucid"
date: 2010-04-29
forum: Education &amp; Science
---

### Post by crislosi on 2010-04-29
Hi! I'm a mathematician and I've made a repository in Launchpad. My objective is having some math programs updated or include some math programs not available in the main repository of Ubuntu
Some packages available:

Carmetal 3.5.2
Geogebra 3.2.41.0
Mathpiperide
wxMaxima 0.8.5
gnuplot 4.4.0

And some math libraries like muparser, lapackpp, sympy, pympl,and gsl.

> GSL only available for 32 bits, no 64 bits because virtual packager machine of Launchpad gives me an error that i can't solve it :(

This is a personal repository, for this reason I've added some alien packages, not math; like: jdownloader, notify-osd patched, ted-television and nicotine+.

To add repository in your Ubuntu Lucid:

```
sudo su -
add-apt-repository ppa:lopeztobal/maths
apt-get update
exit
```

When i have time i'll add more applications, like Octave's new version, Jabref and so on.

Thanks :guitar:

---

### Post by Chronon on 2010-04-30
That's very nice.  Thank you!

---

### Post by koukourikos on 2010-05-26
Very good idea!! Can I propose another package? [SAGE]("http://www.sagemath.org/")  for example? You could also add [Singular]("http://www.singular.uni-kl.de/") and [Axiom]("http://www.axiom-developer.org/"). 
Singular's and Axiom's packages exist at the main repository but they aren't the latest versions

---

### Post by crislosi on 2010-05-26
> **koukourikos said:**
> Very good idea!! Can I propose another package? [SAGE]("http://www.sagemath.org/")  for example? You could also add [Singular]("http://www.singular.uni-kl.de/") and [Axiom]("http://www.axiom-developer.org/"). 
Singular's and Axiom's packages exist at the main repository but they aren't the latest versions

Thanks :-)
Well, sometimes I've repackaged SAGE for Mandriva, and it is very difficult because it has got many many dependencies and always it is very unstable. Perhaps this summer, when i have got more time I package SAGE.
Singular and Axiom can upgrade them next weekend ;-) 
Pay attention ;-)

---

