---
title: "[Howto] make Simulink 6 run (Matlab Version 7.0.0.19901 (R14))"
date: 2007-11-28
forum: Education &amp; Science
---

### Post by phen on 2007-11-28
Hello all,

I didn't find help in these forums, but on a french site. Now I am very proud that I really did understand the french howto. :-) :-D

[Original Thread in french]("http://forum.ubuntu-fr.org/viewtopic.php?pid=1196649")

Since I allready asked in another thread, I want to give you a translation in case anybody else has the same problem.

Problem: when I try to start simulink, matlab crashes with an error that libXft.so.1 is missing. The error is in the first lines of text matlab writes down when it crashes. I didnt record the error message, it is something like:

> Can't load '/usr/local/My_install/matlab/bin/glnx86/libmwsimulink.so': /usr/lib/libXft.so.1: no such file

the following steps assume that matlab is installed in
/usr/local/matlab7


To solve this, follow this:
```

sudo apt-get install libXft2
```

this should install you the libXft.so.2 files.

now link the older libXft.so.1 to the newer files

```
sudo ln -s /usr/lib/libXft.so.2.1.2 /usr/lib/libXft.so.1

```

Now a different error should appear when trying to start simulink:

> ??? Can't load '/usr/local/My_install/matlab/bin/glnx86/libmwsimulink.so': /usr/local/My_install/matlab/bin/glnx86/libqt-mt.so.3: undefined symbol: XftFreeTypeOpen

backup your old qt-mt lib

> sudo mv /usr/local/matlab7/bin/glnx86/libqt-mt.so.3 /usr/local/matlab7/bin/glnx86/libqt-mt.so.3.old

now again another error appears when trying to start simulink.

fix it with

```
sudo mv /usr/local/matlab7/sys/os/glnx86/libgcc_s.so.1 /usr/local/matlab7/sys/os/glnx86/libgcc_s.so.1.old
```

now it works.

hope I could help!

bye

---

### Post by elleP on 2008-03-05
Thank you sir/lady, you are my hero for today.

---

### Post by ravikm on 2008-09-17
thanks a lot. it works on my debian as well.

ravi.

---

### Post by dai_vernon on 2008-09-22
I'm having a really weird problem with simulink on Matlab r2008a (7.6) Everytbing takes about 30 seconds to happen, and when I have objects in my field, I can't double click on them to set their properties.  Has anyone else seen anything like this before?

---

### Post by jeschmitz on 2010-08-18
Thanks! It Works.

---

### Post by vevo on 2012-11-28
On a 64bit ubuntu you need to:

```

sudo mv /usr/local/matlab7/bin/glnxa64/libqt-mt.so.3 /usr/local/matlab7/bin/glnxa64/libqt-mt.so.3.old
```

---

### Post by overdrank on 2012-11-28
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

