---
title: "i can't install AWN on Dapper"
date: 2007-03-21
forum: Desktop Effects &amp; Customization
---

### Post by jfca283 on 2007-03-21
anyone could make it?
i added this repos
```

deb http://download.tuxfamily.org/syzygy42 edgy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 edgy avant-window-navigator
```
but i get problems with some dependencies
so, how is the procedure on Dapper?
thanks

---

### Post by xopher on 2007-03-23
Well, you should expect problems when trying to use a package that isn't build for your system. Your system in this case would be Dapper -- and the system the package is meant for is Edgy.

You basically have two alternatives, build it yourself, or find a repository that's for dapper.

Actually, Ill give you one more option -- upgrade to edgy ;) I mean, if LTS isn't essential, edgy, and feisty in a few weeks, will work for you just as good as dapper does now.

I can't come up with anything smarter to say now, perhaps someone else can.

---

### Post by xflbret on 2007-05-23
a lot of folks have forgotten that LTS means long term support. The ATI folks, and the Beryl folks are two examples of people of have either missed this part or just blatantly disregarded it. I am trying not to go back to windows, but people like those are pushing me. Anyway, point being is that the AWN also forgot what LTS means.

---

### Post by kpolice on 2007-05-23
Try to build it from source, you are trying a 3rd party repository and by no means is an official release.

---

