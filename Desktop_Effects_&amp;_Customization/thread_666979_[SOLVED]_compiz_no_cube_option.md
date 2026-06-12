---
title: "[SOLVED] compiz no cube option"
date: 2008-01-13
forum: Desktop Effects &amp; Customization
---

### Post by Xoanan on 2008-01-13
Hi All

Compiz is installed now and running on metacity themes(apparantly) but I have no option for cube even though it is installed by default as I understand it.

I will screenshot what I have for you

Any ideas? 

Thanx in advance

---

### Post by Xoanan on 2008-01-13
here we go

---

### Post by kbless7 on 2008-01-14
did you do 

```
sudo apt-get install compizconfig-settings-manager
```

in the terminal to the the configuration manager. this will allow you do customize all of that. you barely have anything in there, so try this code

---

### Post by Forlong on 2008-01-14
Post the output of ```
dpkg -l | grep compiz
``` and use the forum's CODE tag please (# button)

---

### Post by Xoanan on 2008-01-14
```
xoanan@ubuntu:~$ dpkg -l | grep compiz
ii  compiz-compcomm-plugins-main               0.0.0+git20070612-0ubuntu1                Collection of plugins from OpenCompositing f
ii  compiz-core                                1:0.6.0+git20071008-0ubuntu1.1            OpenGL window and compositing manager
ii  compiz-switch                              0.2.0~ubuntu                              Easily switch Compiz off and on
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1                Compiz configuration settings manager
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3                Settings library for plugins - OpenCompositi
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1                Compiz configuration system bindings
xoanan@ubuntu:~$
```

---

### Post by ThrobbingBrain66 on 2008-01-14
Instead of compiz-compcomm-plugins-main you want compiz-plugins, compiz-fusion-plugins-extra and compiz-fusion-plugins-main.

---

### Post by Xoanan on 2008-01-14
Yep; and it says its already installed..

---

### Post by Forlong on 2008-01-14
Try this:
```
sudo apt-get remove --purge compiz-compcomm-plugins-main && sudo apt-get install compiz
```

---

### Post by ThrobbingBrain66 on 2008-01-14
> **Xoanan said:**
> Yep; and it says its already installed..

When I run 'dpkg -l | grep compiz' this is the output...yours should look similar:

ii  compiz                                     1:0.6.2+git20071119-0ubuntu1~gutsy1
ii  compiz-core                                1:0.6.2+git20071119-0ubuntu1~gutsy1
ii  compiz-fusion-plugins-extra                0.6.0+git20071121-0ubuntu1~gutsy1
ii  compiz-fusion-plugins-main                 0.5.2+git20070928-0ubuntu2
ii  compiz-gnome                               1:0.6.2+git20071119-0ubuntu1~gutsy1
ii  compiz-plugins                             1:0.6.2+git20071119-0ubuntu1~gutsy1
ii  compizconfig-settings-manager              0.5.2+git20070912-0ubuntu1
ii  libcompizconfig-backend-gconf              0.5.2+git20071010-0ubuntu1
ii  libcompizconfig0                           0.5.2+git20070919-0ubuntu3
ii  python-compizconfig                        0.5.2+git20070912-0ubuntu1

---

### Post by Xoanan on 2008-01-14
Ah! Success all!  Cube works!!

Thanx!:popcorn:

---

