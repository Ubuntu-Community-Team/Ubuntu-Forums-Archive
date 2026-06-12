---
title: "MIT-Scheme 64-bit Package, aptitude weirdness"
date: 2012-03-22
forum: Desktop Environments
---

### Post by DiagonalArg on 2012-03-22
Hi!  Hoping someone can help here ...

If I do 
```
aptitude search mit-scheme
```

I get the following:
```
p   mit-scheme                       - MIT/GNU Scheme development environment    
p   mit-scheme-dbg                   - MIT/GNU Scheme debugging files            
p   mit-scheme-doc                   - MIT/GNU Scheme documentation
```

But if I do 
```
aptitude show mit-scheme
```

It tells me:
```
No current or candidate version found for mit-scheme
Package: mit-scheme
State: not a real package
```

And if I try:
```
aptitude -s install mit-scheme
```

I find:
```
No candidate version found for mit-scheme
No candidate version found for mit-scheme
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Would download/install/remove packages.
```

Confused, I looked around and found that the 64-bit package does exist in Universe:
[http://www.ubuntuupdates.org/package/core/oneiric/universe/base/mit-scheme](http://www.ubuntuupdates.org/package/core/oneiric/universe/base/mit-scheme)

And looking in my /etc/apt/sources.list, universe is indeed uncommented.

So ... what in god's name is going on here?  Anyone with a clue?

Thanks in advance!

---

### Post by Pand5461 on 2012-03-22
> Confused, I looked around and found that the 64-bit package does exist in Universe

It does not. There is "racket" package which provides support for r5rs Scheme.

---

### Post by DiagonalArg on 2012-03-22
PandX, thanks for pointing me to Racket .... 

But what is this link?
[http://security.ubuntu.com/ubuntu/pool/universe/m/mit-scheme/mit-scheme_9.0.1-1ubuntu2_amd64.deb](http://security.ubuntu.com/ubuntu/pool/universe/m/mit-scheme/mit-scheme_9.0.1-1ubuntu2_amd64.deb)

This is found at the link I mentioned above, if you look under "64-bit deb package"
[http://www.ubuntuupdates.org/package/core/oneiric/universe/base/mit-scheme](http://www.ubuntuupdates.org/package/core/oneiric/universe/base/mit-scheme)

(I'm trying to use SICP, by the way, so I want the MIT version. I gather if I were going for "How to Design Programs", then I'd use Racket.)

---

### Post by Pand5461 on 2012-03-22
> But what is this link?
[http://security.ubuntu.com/ubuntu/po...ntu2_amd64.deb](http://security.ubuntu.com/ubuntu/po...ntu2_amd64.deb)
The link doesn't work for me... [Ubuntu packages site]("http://packages.ubuntu.com") also shows only i386 version available, ando so does Synaptic on my machine.

R5RS Scheme (which MIT Scheme is based on) and Racket are very similar. I've done it through the first chapter using Racket, but you always can choose r5rs Scheme from the "Language" menu or use the "use the language declared in source" option and start your program with "#lang r5rs".

---

### Post by DiagonalArg on 2012-03-23
PandX - ... Gee, I suppose I should have clicked on the link before spouting off, huh?  :tongue:  Ok, so perhaps I'll take your advice and try Racket. I also found this link that has a 64 bit .deb. Don't quite know who this guy is though ...
[http://jaiswalayush.blogspot.com/2011/10/install-mit-scheme-on-ubuntu-64-bit.html](http://jaiswalayush.blogspot.com/2011/10/install-mit-scheme-on-ubuntu-64-bit.html)

---

