---
title: "Gambas?"
date: 2004-11-03
forum: Desktop Environments
---

### Post by jts on 2004-11-03
What is the quickest way to get Gambas ([http://gambas.sourceforge.net/download.html](http://gambas.sourceforge.net/download.html))?  I have not found it in universe.  

Still playing around with Ubuntu and don't really want to mess it up by using the Debian package.

---

### Post by FLeiXiuS on 2004-11-03
I found it more appropriate to move this thread to the 'General Support' forum.

Also your best bet would be to download the source tar.bz2 then extract it:

```

tar -xvjf filename.tar.bz2

```

Then you will need to go to the directory created.

```

cd filename

```

Now, thats right compiling time.  To compile follow the following steps.
You can add options to the configurations by type './configure --help' without ' '
```

./configure
make
sudo make install

```

That should install the program for you.  If you encounter any errors during any of the process', then install the needed packages.

By the way, you can acutally install the .deb file by using the dpkg program.
```

dpkg -i filename.deb

```

You can always unistall them afterwards.  I may suggest:
```

man dpkg

```

Note: Just because the files aren't in the apt-get repositories doesn't mean you can't install them.

---

### Post by triad169 on 2004-11-03
Actually the Gambas website has a great installation howto:

[http://gambas.sourceforge.net/tr-compilation.html](http://gambas.sourceforge.net/tr-compilation.html)

Plus they have a Debian repository available for installation via Synaptic.

[http://gambas.sourceforge.net/download.html](http://gambas.sourceforge.net/download.html)

Triad

---

### Post by jts on 2004-11-04
Thank you both, for taking the time to help me out.  I really appreciate it and you are really showing why Ubuntu (in my humble opinion) is different than most other distros.  Ubuntu, seems more newbie/moderate linux user friendly.

Getting back on topic, what version of the DEB package should I chose for gambas?  One is for Sarge and the other is for Woody.  That was my concern in not screwing up my DEB packages.

---

### Post by triad169 on 2004-11-04
just from adding each repostory to my sources.list the woody one has version:

Gambas v. .91-1

and the Sarge One has

Gambas v. .99-1


If you want to live on the wild side I would say go with the sarge one.  But you might break something in the process because it performs alot of upgrades and adds alot of other packages as compared to the woody one.  Both packages install some KDE/Qt dependencies that you can knock out if you manually configure and install youself.  

Triad

---

### Post by meneer on 2005-02-22
Installing fails in synaptic (modules needed but are not installed: gambas-gb-qt but it is not going to be installed and lots more)

Compiling files during configuration time. For instance:
> configure:3750: g++ -c   conftest.cc >&5
./configure: line 1: g++: command not found
configure:3756: $? = 127
configure: failed program was:
| /* confdefs.h.  */
and 
> | 		     Syntax error
configure:7588: /lib/cpp  conftest.cc
cpp: installation problem, cannot exec `cc1plus': No such file or directory
configure:7594: $? = 1
configure: failed program was:
| /* confdefs.h.  */

I'm running a fairly standard 4.10, fully patched.
btw: sources.list entry doesn't feel stable.

Any clue?

---

### Post by Quest-Master on 2005-02-22
Gambas has looked like a fascinating piece of development software, but I am still waiting for the ability to design forms with GTK instead of Qt. :) Plus, Mono's VB.NET looks like competition for it.

I think the reason for..

> 
./configure: line 1: g++: command not found

.. is because you have not yet installed g++, gcc, or build-essential. You can apt-cache search for all of them and install the appropriate packages.

---

