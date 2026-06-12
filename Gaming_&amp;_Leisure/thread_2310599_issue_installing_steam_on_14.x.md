---
title: "issue installing steam on 14.x"
date: 2016-01-20
forum: Gaming &amp; Leisure
---

### Post by pcgamer2426 on 2016-01-20
Helo,

I had to re-install ubuntu and decided to use 14.04. After installation I decided to install steam from the website but, after install it opens a CL to install extra packages and they fail to meet dependencies. I'm not next to it to post the errors but, it was about libcheese6 or so. I did a lil of googling and found diff forum's explaining what to do but, none worked. I have an I7 Nvidia GTX 650 Ti with the drivers 352.

[http://askubuntu.com/questions/588024/steam-install-error-on-14-04-ubuntu-64bit](http://askubuntu.com/questions/588024/steam-install-error-on-14-04-ubuntu-64bit)

---

### Post by oldrocker99 on 2016-01-20
Steam is in the repositories. Try this:```
sudo apt-get install steam
```

It will, or should, install all the dependencies automagically.

---

