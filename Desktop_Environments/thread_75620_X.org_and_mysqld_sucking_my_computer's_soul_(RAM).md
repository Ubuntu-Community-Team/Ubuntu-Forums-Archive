---
title: "X.org and mysqld sucking my computer's soul (RAM)"
date: 2005-10-13
forum: Desktop Environments
---

### Post by DDM on 2005-10-13
So I'm liking breezy so far, aside from the occasional slowdowns due to high RAM usage. Here's a screenshot taken right after bootup. Note that typically x.org takes up more than 240MB 

[img]http://img92.imageshack.us/img92/6992/thesuck6th.png[/img]

and xrestop
[img]http://img92.imageshack.us/img92/2031/ohno5ua.gif[/img]

Is this normal for breezy? Hoary barely cracked 50% ram even with my ftp/ssh/http/samba/mysql stuff.

I realize this isn't a huge problem, but when it started screwing up my BZflag games, then it got SERIOUS.

---

### Post by Amaranth on 2005-10-14
Xorg's memory usage includes however much RAM your video card has, iirc. So subtract that from the value you're getting and you should have something close to the real ammount (although there is no sane way of finding out exactly how much RAM it's using). Check the Resources tab and see how much total RAM and swap is being used, that should be a real ammount.

---

### Post by DDM on 2005-10-14
ah that's reassuring. Now I just gotta find the cause of my intermittent hang-ups.

Thanks.

(Card has 128MB fyi)

---

