---
title: "apt-get, update...nothing works"
date: 2005-06-06
forum: Desktop Environments
---

### Post by byen on 2005-06-06
Hey guys,
Im having serious issues using the apt-get function as it gives me tons of errors... I do not know what is wrong and really need a hand here... here is what my sources.lst says  :
_____________________________________________________________________________________
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

#Primary Mirror (5/17/2005) overloaded :)
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

#backup Mirror - FAST
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

_______________________________________________________________________________________

Is there something I did wrong or something missing.. please help!

And by the way...for the first time in my life..I havnt used... Windoze for 2 months!! How cool must linux be to do that to a person!!!

---

### Post by sethmahoney on 2005-06-06
What errors are you getting?

---

### Post by bored2k on 2005-06-06
Replace your lines with:
> 
_____________________________________________________________________________________
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

#backup Mirror - FAST
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

There were some prohibited repositories.

---

### Post by byen on 2005-06-06
[QUOTE=bored2k]Replace your lines with:

There were some prohibited repositories.[/QUOTE]
 you mean replace my whole sources.list with what you have posted?its pretty much the same isnt it? (sorry if this Q looks ignorant)

---

### Post by bored2k on 2005-06-06
[QUOTE=byen]you mean replace my whole sources.list with what you have posted?its pretty much the same isnt it? (sorry if this Q looks ignorant)[/QUOTE]
 Yes. And no it is not the same. I removed the marillat and ubuntu main repositories wich are 1. Bad for your health and 2. Prohibited -wich means apt wont process.

---

### Post by byen on 2005-06-06
I changed it ran the apt-get update function and it worked!!! thank you BORED2k! this is the second time you saved my day!

---

### Post by bored2k on 2005-06-06
[QUOTE=byen]I changed it ran the apt-get update function and it worked!!! thank you BORED2k! this is the second time you saved my day![/QUOTE]
 Glad to know it worked. Rock on.

---

