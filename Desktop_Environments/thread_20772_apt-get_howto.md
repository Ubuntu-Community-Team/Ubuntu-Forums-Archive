---
title: "apt-get howto"
date: 2005-03-18
forum: Desktop Environments
---

### Post by q(*v*)p on 2005-03-18
Hi,

I'm a linix n**b, and just switched from mandrake to ubuntu, as I like it better.
Now i'd like to install some applications, using apt-get.

for instance, inkscape

so i do this:
sudo apt-get update

reading package lists... done

sudo apt-get install inkscape

reading package lists... done
building dependency tree... done
E: couldn't find package inkscape

It does that by all packages i tried so far, like bluefish and inkscape...?
Any idea what I do wrong?

thanks

---

### Post by dusu on 2005-03-18
Did you make sure that you allow the necessary repositories in your /etc/apt/sources.list file ?

---

### Post by q(*v*)p on 2005-03-18
thanks for the quick reply ;-)
no i didn't, i have a look at it. cheers.

---

### Post by dusu on 2005-03-18
By the way, I forgot, but in case you have more troubles, have a look at
[http://www.ubuntuguide.org/#extrarepositories](http://www.ubuntuguide.org/#extrarepositories)
They tell you what your /etc/apt/sources.list file should look like if you're running warty. If you're running hoary, then replace warty by hoary...

---

### Post by q(*v*)p on 2005-03-18
thanks a lot, it works!!

---

