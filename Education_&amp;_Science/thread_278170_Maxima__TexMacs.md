---
title: "Maxima / TexMacs"
date: 2006-10-15
forum: Education &amp; Science
---

### Post by didobuntu on 2006-10-15
Hello,

I recently discovered Maxima free software ... which under ubuntu can be installed from the repos.

Maxima is a Mapple like ... It do a beautiful job. Moreover, the "wxMaxima" package, also from ubuntu repos, renders it more elegant and very easy to use. I use it in an applied mathematic course .. wonderful.

Also, there is a TexMacs interface, also present in the ubuntu repos, which can render very beautiful LateX reports when exposing Maxima's results.

For the moment I am discovering Maxima .. I think I will never use Mapple anymore.

---

### Post by adamkane on 2006-11-06
TeXmacs + Maxima tutorial:
[http://arxiv.org/html/cs.SC/0504039](http://arxiv.org/html/cs.SC/0504039)

Lyx + Maxima is much more user friendly:
[http://www.jstatsoft.org/v17/s01/v17s01.pdf](http://www.jstatsoft.org/v17/s01/v17s01.pdf)

Lyx + Maxima is a lot like MacKichan Scientific Workplace. They both allow you to type papers, and solve equations at the same time. Very cool.

---

### Post by andreag on 2006-11-24
> **didobuntu said:**
> 

For the moment I am discovering Maxima .. I think I will never use Mapple anymore.

Maxima is great because it is open source. Unfortunately it is far from the level of Maple or Mathematica, try for instance to evaluate algebraically complicated integrals.

However, I am also using Maxima sometimes because I hope development will regain momentum. 

The texmacs interface is also great, but it does not work for me anymore in Edgy, I get 'plug-in maxima not declared' and 'generic maxima program [dead]'. 

Someone has a fix for it? I think it is a problem of compatibility between the versions of maxima and texmacs installed in Edgy.

---

### Post by adamkane on 2006-11-24
No one should really be recommendng Edgy for everyday computing, but here's some helpful info (originally in japanese) via google.

TeXmacs + Maxima + Edgy:
[http://www.a.phys.nagoya-u.ac.jp/~taka/linux/ubuntu610.html](http://www.a.phys.nagoya-u.ac.jp/~taka/linux/ubuntu610.html)

```
[FONT=monospace]
[/FONT]sudo apt-get install texmacs maxima maxima-doc maxima-emacs maxima-share xmaxima 

```

---

### Post by wgrant on 2006-11-24
> **adamkane said:**
> No one should really be recommendng Edgy for everyday computing
[snip]


And why not? It's the latest stable release, and is fine for everyday use.

---

### Post by LaserJock on 2006-11-24
> **adamkane said:**
> No one should really be recommendng Edgy for everyday computing, but here's some helpful info (originally in japanese) via google.

TeXmacs + Maxima + Edgy:
[http://www.a.phys.nagoya-u.ac.jp/~taka/linux/ubuntu610.html](http://www.a.phys.nagoya-u.ac.jp/~taka/linux/ubuntu610.html)

```
[FONT=monospace]
[/FONT]sudo apt-get install texmacs maxima maxima-doc maxima-emacs maxima-share xmaxima 

```

I have to disagree with your point on Edgy. We fixed many things in Edgy that were problems in Dapper (maxima frontend breakage, for instance). We also got updated packages like Scipy and Numpy. I think Dapper's probably better for servers and corporates because of the longer support, but other than that I don't see much of a reason to not recommend Edgy. Sticking with Dapper might also make upgrading to Feisty a bit more difficult.

-LaserJock

---

### Post by andreag on 2006-11-25
> **adamkane said:**
> No one should really be recommendng Edgy for everyday computing, but here's some helpful info (originally in japanese) via google.

TeXmacs + Maxima + Edgy:
[http://www.a.phys.nagoya-u.ac.jp/~taka/linux/ubuntu610.html](http://www.a.phys.nagoya-u.ac.jp/~taka/linux/ubuntu610.html)

```
[FONT=monospace]
[/FONT]sudo apt-get install texmacs maxima maxima-doc maxima-emacs maxima-share xmaxima 

```

I already have all these packages, but the maxima frontend is broken all the same :( 

I had no real problems with Edgy, I think it is a stable enough release.

However, the texmacs and maxima versions in Edgy are not so new, is it not possible to backport newer versions?

Finally, not only maxima detection is broken with texmacs, but also detection of maple and mupad (the sessions are declared "dead").

Detection of axiom, gnuplot, octave, python, R, scilab, shell, yacas works.

---

### Post by andreag on 2006-11-25
> **LaserJock said:**
> I have to disagree with your point on Edgy. We fixed many things in Edgy that were problems in Dapper (maxima frontend breakage, for instance). We also got updated packages like Scipy and Numpy. I think Dapper's probably better for servers and corporates because of the longer support, but other than that I don't see much of a reason to not recommend Edgy. Sticking with Dapper might also make upgrading to Feisty a bit more difficult.

-LaserJock

I agree, Edgy is ok. But you say that the maxima frontend now works... you mean texmacs frontend for maxima or maxima own graphic frontend? the texmacs frontend is broken for me, see above. Do you have suggestions on how to fix it?

I suspect there is some problem here:

$ /usr/lib/texmacs/TeXmacs/bin/maxima_detect
#f 

$ $MAXIMA --list-avail
Available versions:
version 5.9.3, lisp gcl

that is, maxima_detect does not detect any version of maxima on my Edgy box, although there is one.

---

### Post by andreag on 2006-11-25
Apparently the broken maxima frontend is a known bug in Edgy, and the solution is an easy one, see

[https://launchpad.net/distros/ubuntu/+source/texmacs/+bug/58498](https://launchpad.net/distros/ubuntu/+source/texmacs/+bug/58498)

---

### Post by junglepeanut on 2006-11-25
Also I think you have to do some change from 5.9 to 5.10. I cant remember exactly what I did but this was part of the issue as well I found the suggestion from google so you should be able to search it. I ended up unistalling texmacs so I can't tell you what I had in those files, I liked maxima better with out the frontend. Much better I think.

---

### Post by asoto on 2006-12-06
Here is a fix:

In the file maxima_detect, change #!/usr/bin/sh to #!/usr/bin/bash

And it should work (the reason is that it seems that in edgy sh is no longer the same as bash, and grep does not work in the same way)

---

### Post by asoto on 2006-12-06
maxima_detect is in the directory 

plugins/maxima/bin/

you should be able to edit this file, even if you only installed the binary.

---

### Post by Rui Pais on 2007-02-01
hi,
i discover this thread by searching the forum looking for an answer for a (kind of) related problem. 
So i post here, for the case someone got the same question...

(This damn shell change had give more headaches then any visible advantage...)

Any time i tried to make a plot on gnuplot plugin i've got something like: 
'-E reset. command bla, bla, bla...' 

Of course another shell issue.

In this case one needs to apply the above "trick" (change #!/bin/sh to #!/bin/bash) to the file **tm_gnuplot** 
(by default on edgy at: /usr/lib/texmacs/TeXmacs/bin/)

---

