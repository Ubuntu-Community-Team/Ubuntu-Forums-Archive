---
title: "DVD-R support???"
date: 2005-12-10
forum: General Help
---

### Post by justinjstark on 2005-12-10
I bought a lite-on dvd burner and a 25 spindle of dvd-r's but when I go to burn using nautilus cd burning it says, "Please put a CD-R/CD-RW/DVD-RW/DVD+R/DVD+RW, with at least xxxx MiB free, into the drive."

Am I out $9 for the dvd's and need to get some dvd+r's????

---

### Post by taurus on 2005-12-10
I don't think so.  Have you tried them with k3b?  Personally, I've never liked nautilus as my file manager so I wouldn't use it to burn anything.  I always use k3b if I want to burn something but if you don't like KDE app, then try graveman then!

---

### Post by Adrian on 2005-12-10
[QUOTE=blaksaga]I bought a lite-on dvd burner and a 25 spindle of dvd-r's but when I go to burn using nautilus cd burning it says, "Please put a CD-R/CD-RW/DVD-RW/DVD+R/DVD+RW, with at least xxxx MiB free, into the drive."

Am I out $9 for the dvd's and need to get some dvd+r's????[/QUOTE]

What model is it, more specifically?

---

### Post by justinjstark on 2005-12-10
[QUOTE=Adrian]What model is it, more specifically?[/QUOTE]

[http://www.newegg.com/Product/Product.asp?Item=N82E16827106988]("http://www.newegg.com/Product/Product.asp?Item=N82E16827106988")

It supports both formats at 16x.

Also, I am really starting to like the nautilus cd burner.  I've used it to burn data cds for a while now and the whole drag-n-drop built-in-to-the-filemanager scheme works beautifully.

---

### Post by Adrian on 2005-12-10
[QUOTE=blaksaga][http://www.newegg.com/Product/Product.asp?Item=N82E16827106988]("http://www.newegg.com/Product/Product.asp?Item=N82E16827106988")

It supports both formats at 16x.[/QUOTE]

Well, it shouldn't be the problem then. I'd try K3b, as taurus suggested.

---

### Post by justinjstark on 2005-12-10
Well, it works fine in gnomebaker which I already had installed.  I'd really like to get it working in nautilus...or else I'll just pick up some dvd+r's (maybe the backend to nautilus-cd-burner doesn't support dvd-r's?) and try them out.

---

### Post by teaker1s on 2005-12-10
make sure you have any dependencies installed for instance gnomebaker needs cdrecord

---

### Post by taurus on 2005-12-10
[QUOTE=teaker1s]make sure you have any dependencies installed for instance gnomebaker needs cdrecord[/QUOTE]
I thought they (if not most of them) need cdrecord!!!

---

### Post by teaker1s on 2005-12-10
true and there is libdvdread3 for reading dvd's too

---

### Post by justinjstark on 2005-12-10
Nevermind...it does work.  It's just that nautilus won't burn it when I have >4.4gb even on a 4.7gb disc.  :???:  errrr...

Thanks for trying to help though, everybody!  ;)

---

### Post by Adrian on 2005-12-10
[QUOTE=blaksaga]Nevermind...it does work.  It's just that nautilus won't burn it when I have >4.4gb even on a 4.7gb disc.  :???:  errrr...

Thanks for trying to help though, everybody!  ;)[/QUOTE]

Nice! I'm glad to see that you sorted it out.

You probably already know this, but I say it anyway :)
By experimenting, I've come to the following conclusion: A DVD-R holds 4 700 000 000 bytes, i.e. one kilobyte is defined as 1000 bytes.

This is not the proper definition of 4.7GB, since one kilobyte is 1024=2^10 bytes and not 1000 bytes. Similary a gigabyte is 2^30=1 073 741 824 bytes.
Using this definition, a disc can hold approximately 4.4GB of data.

When I'm burning, I always count bytes and not gigabytes :)

Edit: "Proper" is probably the wrong word here, since both definitions seem to be accepted (or actually, the first one seems to be more accepted, than the "proper" one :) ). "Different" is a better word, I guess. Read more about it [here]("http://en.wikipedia.org/wiki/Gigabyte")

---

### Post by justinjstark on 2005-12-10
[QUOTE=Adrian]Nice! I'm glad to see that you sorted it out.

You probably already know this, but I say it anyway :)
By experimenting, I've come to the following conclusion: A DVD-R holds 4 700 000 000 bytes, i.e. one kilobyte is defined as 1000 bytes.

This is not the proper definition of 4.7GB, since one kilobyte is 1024=2^10 bytes and not 1000 bytes. Similary a gigabyte is 2^30=1 073 741 824 bytes.
Using this definition, a disc can hold approximately 4.4GB of data.

When I'm burning, I always count bytes and not gigabytes :)

Edit: "Proper" is probably the wrong word here, since both definitions seem to be accepted (or actually, the first one seems to be more accepted, than the "proper" one :) ). "Different" is a better word, I guess. Read more about it [here]("http://en.wikipedia.org/wiki/Gigabyte")[/QUOTE]


That's a nice little tidbit to know.  My discs are not 4.7gb like it says on the disc but rather ~4.4.  So nautilus calculates it right but not the dvd manufacturers :mad: .  Thanks for the explanation.

---

