---
title: "SimCity 3000 glibc-2.1 Problems"
date: 2009-04-13
forum: Gaming &amp; Leisure
---

### Post by Neurosynapse on 2009-04-13
Hello Again!

I was attempting to install SimCity 3000 for Linux on my system, and this is the error I get:
```
This installation doesn't support glibc-2.1 on Linux / x86

Please contact Loki Technical Support at support@lokigames.com
```
Anyone have any ideas on what I can do to get the setup.sh to run?

Thanks in advance!
Neuro

---

### Post by translucent juicebox on 2009-04-29
I'm having this exact same problem and google isn't helping me much, so someone please help both of us.

---

### Post by AthlonMDK on 2009-05-01
Hi

Try this might help there seems to be an glibc incompatiblity issue

[http://www.gentoo-wiki.info/HOWTO_Running_Old_Loki_Games#Sim_City_3000](http://www.gentoo-wiki.info/HOWTO_Running_Old_Loki_Games#Sim_City_3000)

---

### Post by translucent juicebox on 2009-05-02
In that link, what does this mean?...

Make a file containing:

49,52c49,52
< [ $sum1 -ne $CRCsum ] && {
<   echo Error in checksums $sum1 $CRCsum
<   exit 2;
< }
---
> #[ $sum1 -ne $CRCsum ] && {
> #  echo Error in checksums $sum1 $CRCsum
> #  exit 2;
> # }
118,121c118,121
< [ $sum1 -ne $CRCsum ] && {
<   $echo Error in check sums $sum1 $CRCsum
<   eval $finish; exit 2;
< }
---
> #[ $sum1 -ne $CRCsum ] && {
> #  $echo Error in check sums $sum1 $CRCsum
> #  eval $finish; exit 2;
> #}
140c140
< [ "$keep" = y ] || trap 'cd /tmp; /bin/rm -rf $tmpdir; exit $res'
---
> [ "$keep" = y ] || trap 'cd /tmp; /bin/rm -rf $tmpdir; exit $res' 0 

Do they mean that I'm supposed to copy and paste that into a text document when they say make a file, or am I to type that into terminal, or what?  I'm not very computer savvy.

---

### Post by rottenart on 2010-04-20
Bump. Help anyone?

---

### Post by ELD on 2010-04-21
[http://ubuntuforums.org/showpost.php?p=9153595&postcount=5](http://ubuntuforums.org/showpost.php?p=9153595&postcount=5)

---

