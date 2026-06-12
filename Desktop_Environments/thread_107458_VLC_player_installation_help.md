---
title: "VLC player installation help"
date: 2005-12-23
forum: Desktop Environments
---

### Post by index_0@ya.com on 2005-12-23
Hi thr ..
    When i ty to compile VLC player source code , I get the foll err ,   
 ...
checking for ffmpeg/avcodec.h... no
configure: error: Missing header file ffmpeg/avcodec.h

I also got an error saying a plugin called 'mad' was missing ,which skipped thru the configure options .. 
Did not VLC supply the header file for compilation ?

Pls help. ..

---

### Post by Ocxic on 2005-12-23
use synaptic to get wxvlc

---

### Post by index_0@ya.com on 2005-12-23
And this is probably the reason tht seperates 
user-freindliness of linux and Windows ..
Wht does a newbie like me do >>
dont they know tht they should distribute the compiled version ???

---

### Post by Perfect Storm on 2005-12-23
Linux is a world to diffrent than windows and can be hard to learn the way, but in the end it's very rewarding.

The reason there isn't a compiled version is that there's many diffrent linux distro out there with its own unique setup.
For a newbie it will be better to use synaptic package manager to install the application you want. 

See here how to setup you source list: [http://doc.gwos.org/index.php/Sources.list](http://doc.gwos.org/index.php/Sources.list)

remember to run
```
sudo apt-get update
```
afterwards

---

