---
title: "Subsurface installation and usage on Ubuntu"
date: 2013-12-03
forum: Gaming &amp; Leisure
---

### Post by Berduchwal on 2013-12-03
I have installed Subsufrace application from standard Ubuntu repository on 13.04.

It works ok out of the box apart from several small issues.

My dive computer Suntoo HelO2 when connected is not properly captured by the program.

When I try I get message saying that it is unable to access dev/usbtty0. This can be fixed by runing subsurface from the terminal using sudo as a root user.

This is not particularly wise but this is also the only way to have map working. Those issues I guess are to do with permission of the packages and can be fixed by the maintainer.

[https://launchpad.net/~subsurface/+archive/subsurface]("https://launchpad.net/~subsurface/+archive/subsurface")

New version 3.9.1 came out few days ago I hope it will be packaged soon.

===Edit===

There is a repository which contains new version:
```
sudo add-apt-repository ppa:subsurface/subsurface
```

To avoid running app as a root do:
```
sudo adduser [username] dialout
```

---

