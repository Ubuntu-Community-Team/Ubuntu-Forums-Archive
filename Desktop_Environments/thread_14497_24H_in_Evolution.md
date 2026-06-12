---
title: "24H in Evolution"
date: 2005-02-07
forum: Desktop Environments
---

### Post by hindiogine on 2005-02-07
I just succesfully converted from Fedora3 to Ubuntu 4.10.   Love it!  It is faster than FC3.

There is just 1 thing that I do not like:  I used Kontact and I like to display the timestamp of the email in the email list in 24H format and not AM/PM.  I could do so in Kontact.  How to do so in Evolution?

Thanks in advance.

hindiogine

---

### Post by nocturn on 2005-02-08
[QUOTE=hindiogine]I just succesfully converted from Fedora3 to Ubuntu 4.10.   Love it!  It is faster than FC3.

There is just 1 thing that I do not like:  I used Kontact and I like to display the timestamp of the email in the email list in 24H format and not AM/PM.  I could do so in Kontact.  How to do so in Evolution?

Thanks in advance.

hindiogine[/QUOTE]

Evolution relies on your locale for that.  If your locale defaults to 12h, Evolution will do so to.    Just set your locale either correctly, or to a value that uses 24h, and Evolution will follow.

---

### Post by hindiogine on 2005-02-08
Thanks for the explanation.  Could you please explain how to  change the locale?

I hate to admit it, but I know how to do so in Win9x, but not in Ubuntu Linux.

Shamefully yours,

hindiogine

 :confused:

---

### Post by nocturn on 2005-02-09
[QUOTE=hindiogine]Thanks for the explanation.  Could you please explain how to  change the locale?

I hate to admit it, but I know how to do so in Win9x, but not in Ubuntu Linux.

Shamefully yours,

hindiogine

 :confused:[/QUOTE]

Don't worry about it, everyone was new to Linux at one point at least ;-)
One sidenote, the locale sets up several things, including your language, time display, currency, ...   So make sure you pick one that fits you (I always pick an English language even though my language is Dutch).

In a terminal, run
dpkg-reconfigure locales
locale-gen

In dpkg-reconfigure, make sure you select a valid locale for you and make it the default.

Now logout and in again

---

### Post by hindiogine on 2005-02-09
Dank je wel nocturn!

Worked very well.   

Of course use sudo before each command and then logout->login.

I used en_GB and now I have 24H in evolution.

I am liking Ubuntu more and more.


hindiogine

---

