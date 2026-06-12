---
title: "apt-get and yum"
date: 2009-04-06
forum: General Help
---

### Post by d0.higgs on 2009-04-06
Hi all,

I just made the transition from Fedora to Ubuntu. I am happy with Ubuntu, it has changed a lot. U-8.10 is very good indeed.

I have this question about apt-get:

When using yum (from the console) the layout is very nice and very informative and it gives you a summary of changes that will take place and a list of the packages that will be installed and another list of those to be installed for dependency.

apt-get works fine, yet it is not as tidy and as neat as yum (although yumex, the GUI of yum is too far away behind synaptic, yet I am a console guy), so my question is: (and my apology if this is not the right place, I am still new to Ubuntu world) Is there a way to adjust apt-get behavior? And if not, whom should I talk to for such a suggestion?

Thank you so much,

bye

---

### Post by nikgare on 2009-04-06
try **aptitude** instaed

---

### Post by d0.higgs on 2009-04-07
Hi,

Thanks for the reply.
I tried aptitude and it almost gave me the same behavior. This is what I used:

$sudo aptitude install kwrite.

As I said, although synaptic is far more better than yumex, yet the layout of yum is more informative that apt-get (aptitude). I believe it is an easy thing to add to either apt-get or aptitude.

Thanks again,

bye

---

### Post by Cheesemill on 2009-04-07
I think that nikgare meant to try
```
aptitude
```
without any arguments.
This will fire up an ncurses interface for aptitude.

Cheesemill

---

