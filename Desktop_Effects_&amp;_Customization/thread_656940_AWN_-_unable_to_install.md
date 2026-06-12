---
title: "AWN - unable to install"
date: 2008-01-03
forum: Desktop Effects &amp; Customization
---

### Post by drw1978 on 2008-01-03
When trying to install avant window manager I get the following message:

[B]avant-window-navigator-bzr:
 Depends: libawn-bzr but it is not going to be installed
  Depends: libpango1.0-0 (>=1.18.3) but 1.18.2-0ubuntu1 is to be installed
 Depends: libawn-bzr but it is not going to be installe[/B]

I have tried installing the libawn & libpango files but they also depend on one another so I cant install any of them!

whats going on?

---

### Post by Mr Greencastle on 2008-01-03
Can you run this in a terminal?
```
sudo apt-get install -f
```

---

### Post by alsamman on 2008-01-03
lol I had this exact same problem yesterday and I got AWN working. What I did was follow steps here: [http://ubuntuforums.org/showthread.php?t=385981](http://ubuntuforums.org/showthread.php?t=385981) and it got working. Remove the repositories and make sure you don't have any part of awn installed (for me I had to remove libawn0).

---

