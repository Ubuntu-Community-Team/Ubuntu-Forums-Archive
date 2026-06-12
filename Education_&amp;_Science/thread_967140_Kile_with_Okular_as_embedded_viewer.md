---
title: "Kile with Okular as embedded viewer"
date: 2008-11-01
forum: Education &amp; Science
---

### Post by marvin777 on 2008-11-01
Does anyone know how to get kile to use Okular as en embedded viewer?  Searching on Google, I saw reference to 'libokularpart' but I don't seem to have that library.  I'm running Ubuntu 8.1 and I compile kile (2.0.2) myself from the sources since the packaged version insists on installing texlive 2007 and I'm a texlive 2008 user.  I use to use the kpdf package for this purpose, but it seems to have vanished once I upgraded to Intrepid.

Thanks,
 - marvin

---

### Post by ghatfan99 on 2008-11-02
hello
first excuse me for my english, 
kile -> configuration -> configuration kile  -> tools -> compilation -> after that you can choose an tool en change her configuration at the right
for exemple:
tool = view pdf
----> new configuration ---> choose an configuration= okular
                             command= okular

and the same thing for the restes 
view ps
bye

---

### Post by marvin777 on 2008-11-02
Thats works for setting up okular as an external viewer, but I want to set it up as in embedded viewer within kile like I had with kpdf.

Thanks!

---

### Post by &#1497;&#1493;&#1505;&#1497; &#1490;&#1497;&#1500; on 2008-11-20
> **marvin777 said:**
> ....  I'm running Ubuntu 8.1 and I compile kile (2.0.2) myself from the sources since the packaged version insists on installing texlive 2007 and I'm a texlive 2008 user...

Any tips on how you compiled? Which --prefix you used? And, which KDE package did you install so that it finds the KDE libraries?

---

### Post by marvin777 on 2008-11-30
prefix was /usr/local

I compiled it against the kde3 dev packages loaded via synaptic.  I'm away from that machine for the next few days -- will add more details here when I'm on that machine.

---

### Post by alberto_m on 2008-12-02
I'm so eager to have more details!
Thanks!

---

