---
title: "compiz cube plugins ubuntu 12.04"
date: 2012-11-06
forum: Desktop Environments
---

### Post by Hedgehog9597 on 2012-11-06
I apologize in advance for creating this thread; I tried to post my question in the sticky, but the thread was closed...

So, I am trying to get cube caps to work with ubuntu 12.04.  More generally, I'm trying to install this plugin: [http://wiki.compiz.org/PluginsExtra](http://wiki.compiz.org/PluginsExtra)

because it has lots of nice little tweaks.

Is this possible in ubuntu 12.04? Here's what I did in terminal:

```

x@x:~$ mkdir compiz
x@x:~$ cd compiz
x@x:~/compiz$ git clone git://anongit.compiz.org/fusion/plugins-extra
Cloning into 'plugins-extra'...
remote: Counting objects: 5905, done.
remote: Compressing objects: 100% (2909/2909), done.
remote: Total 5905 (delta 4230), reused 4124 (delta 2939)
Receiving objects: 100% (5905/5905), 5.17 MiB | 168 KiB/s, done.
Resolving deltas: 100% (4230/4230), done.
x@x:~/compiz$ cd plugins-extra
x@x:~/compiz/plugins-extra$ make
make: *** No targets specified and no makefile found.  Stop.
x@x:~/compiz/plugins-extra$ make -f Makefile.am
Makefile.am:12: *** missing separator.  Stop.

```

What can I do from here?

Thanks,
hedgehog

---

### Post by zombifier25 on 2012-11-06
The Extra Plugins are in Ubuntu's repos. Install compiz-plugins-extra.

---

