---
title: "Apt-get from CD ?"
date: 2006-07-15
forum: Desktop Environments
---

### Post by seshomaru samma on 2006-07-15
Hi
I succesfully installed Ubuntu on an old computer with very slow internet connection . I would like to apt-get install several things but some of them are VERY big (like Chinese support) and would take years with a slow connection. I was wondering if theres anyway to apt-get them on another Ubuntu ,burn them to a CD and run them on the slow-connection machine?

Is it possible to prepare a CD with all my favourite programmes so that each time I install Ubuntu I dont have to spend time in downloading them ?

---

### Post by Ramses de Norre on 2006-07-15
Take a look at [this]("http://mylifeasasoftwaretester.blogspot.com/2006/06/creating-local-ubuntu-mirror.html").

---

### Post by iwagner on 2006-07-18
I'm glad to see that my blog is useful. Thanks for posting that link.

The answer to your question is yes.  Set up a mirror repository on one machine, burn that mirror to DVD (or many DVD's), and then in your sources.list for apt you would specify the path to the repository with a file://path/to/repo instead of [http://some.server](http://some.server).

---

### Post by seshomaru samma on 2006-08-12
Since I only need a few packages , what I did was go to :
var/cache/apt/archives and copied the deb. files I needed to a USB drive and then installed them manually.

Thanks for help ,anyway!

---

### Post by az on 2006-08-12
[https://help.ubuntu.com/community/AptMoveHowto](https://help.ubuntu.com/community/AptMoveHowto)
or
[https://help.ubuntu.com/community/AptMoveHowto/simple](https://help.ubuntu.com/community/AptMoveHowto/simple)

---

### Post by seshomaru samma on 2006-08-12
That's great , thanks

---

