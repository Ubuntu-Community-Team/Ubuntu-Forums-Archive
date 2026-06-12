---
title: "Dell Mini 10:  Not finding lgthread-2.0 on Ubuntu 8.04"
date: 2009-10-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by McSnickered on 2009-10-30
Greetings,

I just bought a Dell Mini 1011 with Ubuntu 8.04.  It's really fun and I'm glad I went with Linux.

One problem I've run into:  I installed Qt Creator, but I'm not able to compile any programs with it.  The compile output says "Can't find lgthread-2.0".  I thought lgthread-2.0 might be in the libglib2.0-dev package, but apt-get fails when trying to install it.

I'd be grateful for any help you can offer!

---

### Post by McSnickered on 2009-11-10
I was finally able to get things working.  I found some great help at the following blog:

--------------
[http://blog.dixo.net/2009/03/14/using-qt-creator-with-ubuntu-810/](http://blog.dixo.net/2009/03/14/using-qt-creator-with-ubuntu-810/)

Installation of Qt Creator under Ubuntu 8.10 is straightforward, but I’m writing this post just to note the install steps I took. Hope it helps someone!

    * Download and install the SDK, which includes an IDE
    * Once installed, there’s a few packages you’ll need to ensure your first build completes:
    * sudo apt-get install libfreetype6-dev libfontconfig-dev libxrender-dev libsm-dev libglib2.0-dev
   * sudo apt-get install libxext-dev libxext6-dbg x11proto-xext-dev 
-----------

I was able to run Qt Creator on my Dell Mini 1011 and it works quite well.  The small screen makes it a little difficult to do form designing but it is possible.  Editing code is fine on the small screen and compile time is not unbearable.  All in all, it works pretty well!

---

