---
title: "choosing where apt puts files - possible?"
date: 2005-12-08
forum: General Help
---

### Post by ponkan on 2005-12-08
Hello, I was wondering if there's any way to set apt up so that I can choose where the binaries go. I realize that it would probably be much easier if I simply compiled from source, but doing that doesn't allow me to keep track of what I installed, as well as resolve dependencies with the ease that apt does.

---

### Post by MartinG on 2005-12-08
Why do you want to?

I don't think it is possible, but in any case it seems to me to be a r-e-a-l-l-y bad idea to try and install elsewhere than where the maintainers have put it, as this could lead to all sorts of dependency problems later on, as later packages expect to find things in certain, standard, places.  If you're enough of a Linux expert to know what you're about in trying to do this, then you should already know enough not to need to ask this question :-)

---

### Post by ponkan on 2005-12-08
Basically just choosing whether the binaries are going into /usr or /usr/local.

---

### Post by taurus on 2005-12-08
Most of the time when you compile something from source, the binary (or binaries) will go into /usr/local/bin!  However, you can change the path when you run ./configure...

---

