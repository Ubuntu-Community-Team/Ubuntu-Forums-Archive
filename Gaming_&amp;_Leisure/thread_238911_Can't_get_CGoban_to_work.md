---
title: "Can't get CGoban to work"
date: 2006-08-18
forum: Gaming &amp; Leisure
---

### Post by mauro007 on 2006-08-18
I'm tring to install CGoban
[http://www.igoweb.org/~wms/comp/cgoban/index.html](http://www.igoweb.org/~wms/comp/cgoban/index.html)
I tried to compile it from source code but it gave me an error saying that there wasn't an acceptable cc found in $PATH. I then installed the buld-essentials including the cvs subversion, just to get another error:

"Sorry, configure cannot find your X includes and libraries.
*** Compiling cannot continue until this is fixed.
*** If you know where your X11 is installed, try
***   ./configure --x-includes=<DIR> --x-libraries=<DIR>"

Can anyone help me?

Thanks

---

### Post by Perfect Storm on 2006-08-18
```
sudo aptitude install xlibs-dev
```


If you have universe enable in your sourcelist, you can just easely do this:
```
sudo apt-get install cgoban
```

---

### Post by mauro007 on 2006-08-18
Thanks, it works!
Pity I can't play against it, it only supports game servers and not a local engine.

---

### Post by seb_renaud on 2006-11-06
You can play against gnugo ( universe ) locally. Select Go Modem, make one player "Human" and the other "Program". It should default to gnugo with the appropriate switches. man gnugo will give you ( very little ) more info about playing gnugo with cgoban. Enjoy!

---

### Post by Hicksrules on 2009-03-06
Hi

I also have Cgoban but cannot play against the program.  I have done what was instructed (select one player human and the other program , did not tamper with the defaults but cannot lay down a single stone.

Can someone help!

---

