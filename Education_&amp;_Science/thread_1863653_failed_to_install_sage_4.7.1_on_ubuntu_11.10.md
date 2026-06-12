---
title: "failed to install sage 4.7.1 on ubuntu 11.10"
date: 2011-10-18
forum: Education &amp; Science
---

### Post by surfer on 2011-10-18
i downloaded sage from sagemath.org ( sage-4.7.1-linux-64bit-ubuntu_10.04.1_lts-x86_64-Linux ), unpacked it and tried to do the first run as root. this produced the following error message:

```
$ sudo ./sage/sage 
----------------------------------------------------------------------
| Sage Version 4.7.1, Release Date: 2011-08-11                       |
| Type notebook() for the GUI, and license() for information.        |
----------------------------------------------------------------------
Traceback (most recent call last):
  File "/opt/sage/local/bin/sage-ipython", line 18, in <module>
    import IPython
  File "/opt/sage/local/lib/python2.6/site-packages/IPython/__init__.py", line 58, in <module>
    __import__(name,glob,loc,[])
  File "/opt/sage/local/lib/python2.6/site-packages/IPython/ipstruct.py", line 22, in <module>
    from IPython.genutils import list2dict2
  File "/opt/sage/local/lib/python2.6/site-packages/IPython/genutils.py", line 59, in <module>
    from IPython.external.path import path
  File "/opt/sage/local/lib/python2.6/site-packages/IPython/external/path.py", line 35, in <module>
    import md5
  File "/opt/sage/local/lib/python/md5.py", line 10, in <module>
    from hashlib import md5
  File "/opt/sage/local/lib/python/hashlib.py", line 136, in <module>
    md5 = __get_builtin_constructor('md5')
  File "/opt/sage/local/lib/python/hashlib.py", line 63, in __get_builtin_constructor
    import _md5
ImportError: No module named _md5

```

any ideas how this could be fixed?

---

### Post by grappler on 2011-10-18
I can report that an attempt to compile the source code 

sage-4.7.1-linux-64bit-ubuntu_10.04.1_lts-x86_64-Linux.tar.lzma

on a new installation of  the official release of ubuntu 11.10

gives the same error


> ImportError: No module named _md5
make: *** [doc-html] Error 1

---

### Post by vibration on 2011-10-27
I had the same issue. After installation of the package libssl0.9.8 it compiled without error.

---

### Post by ptg21 on 2011-10-27
Thanks so much for your post - very much appreciated!

---

### Post by grappler on 2011-10-27
Thanks Vibration - works perfectly!

---

### Post by MentatGhola on 2011-11-03
Aye I had the same error and sure enough installing libssl0.9.8 fixed it.

---

### Post by PGScooter on 2011-11-03
It's great to see all of the confirmed reports of success. It's always nice when someone takes a little time to confirm a solution.

I've had several installs be fixed by non-obvious packages like this. Is this considered a bug? if so, whom do we report it to? I'm guessing SAGE, but would they be interested?

---

### Post by meng1usa on 2011-11-05
libssl0.9.8 that works! finally! Thank you!

---

### Post by surfer on 2011-12-15
late reply. sorry.

indeed:
```
$ sudo apt-get install libssl0.9.8
```
is all it takes to get sage sage-4.7.1-linux-64bit-ubuntu_10.04.1_lts-x86_64-Linux running on oneiric!

thanks vibration and everyone who posted a success report!

marking the thread solved.

---

### Post by rtalcott on 2012-01-05
**Vibration:**
Thank You!  I have never had this issue before and I greatly appreciate the solution!
rt

---

### Post by crazy ivan on 2012-01-09
Thanks for the solution.
Just wanted to let you know, that this works for sage-4.7.**2**-linux-64bit-ubuntu_10.04.3_lts-x86_64-Linux as well!

---

### Post by ferdiaz on 2012-01-19
> **vibration said:**
> I had the same issue. After installation of the package libssl0.9.8 it compiled without error.

It worked. Thanks!

---

### Post by surfer on 2012-02-08
the compiled version of [FONT="Courier New"]sage 4.8[/FONT] runs (again, with [FONT="Courier New"]libssl0.9.8[/FONT] installed) on ubuntu 12.04 as well!

---

### Post by NahsiN on 2012-04-06
Thanks libsssl0.9.8 did the trink

---

### Post by pietrucha23 on 2012-04-25
> **surfer said:**
> the compiled version of [FONT="Courier New"]sage 4.8[/FONT] runs (again, with [FONT="Courier New"]libssl0.9.8[/FONT] installed) on ubuntu 12.04 as well!

Sage usually has an official release just for LTS Ubuntu. And 12.04 will be one. So hopefully in May 2012 we will have Sage working out the box on 12.04.

---

### Post by PGScooter on 2012-05-08
> **pietrucha23 said:**
> Sage usually has an official release just for LTS Ubuntu. And 12.04 will be one. So hopefully in May 2012 we will have Sage working out the box on 12.04.

What do you mean by out the box? PPA? deb? in the repos for 12.04.1?

I'll be looking forward to it. Thanks!

Also, do you think that compiling by source will lead to performance advantages?

---

### Post by PGScooter on 2012-05-17
Note that on 12.04, I did not need to install libssl. Everything worked smoothly. See here
[http://ubuntuforums.org/forumdisplay.php?f=169](http://ubuntuforums.org/forumdisplay.php?f=169)
also, all of the tests from `make test` passed.

---

### Post by surfer on 2012-05-18
Also sage 5.0 can be donwnloaded and unzipped (again: the compiled version, no make needed) and works.

did anyone try the PPA [ppa:aims/sagemath]("https://launchpad.net/~aims/+archive/sagemath") ?

(also compare with [this thread]("http://ubuntuforums.org/showthread.php?t=1981334")).

---

### Post by rtalcott on 2012-05-18
trying to install the binary for Ubuntu... worked before on pr 12.04 versions...now I am getting:
**ImportError: cannot import name md5**

I'm certain it's something simple I am just not sure what...any ideas?
thanx
rt

---

### Post by surfer on 2012-05-18
up to now, this always worked for me:

```
$ sudo apt-get install libssl0.9.8
```

is this no longer the case for sage 5.0?

---

### Post by rtalcott on 2012-05-18
Will give this a try...Thank You!
rt

---

### Post by rtalcott on 2012-05-18
Thank you...that worked for me...I did not realize that I still needed to do this for 12.04/Sage 5.
rt

---

### Post by surfer on 2012-05-18
welcome!

happy sageing! (...well)

---

### Post by rtalcott on 2012-05-18
I should have reread this thread!  I had read in another thread that this was not needed BUT I should have tried it anyway...so...accept my apology for having my head up my a**!
rt

---

### Post by PGScooter on 2012-05-19
> **rtalcott said:**
> I should have reread this thread!  I had read in another thread that this was not needed BUT I should have tried it anyway...so...accept my apology for having my head up my a**!
rt

I guess this is my fault, although I did not say that it wasn't needed. I said that *I* did not need to do it.

Upon futher investigation, it's true that I don't have libssl0.9.8 installed but I do have libssl1.0.0 installed (both are in the precise repos for me). So I guess you have the choice. I'm not sure which one is better to install but maybe 1.0.0 is better because it's a later version.

In any case, someone should really send an email to the sage email list:
[https://groups.google.com/forum/?fromgroups#!forum/sage-support](https://groups.google.com/forum/?fromgroups#!forum/sage-support)

because I search for libssl only shows one messsage so I don't think they are aware of this issue. I'm not going to send the email because I did not have this problem in 12.04. For me, everything worked as the instructions said.

---

### Post by surfer on 2012-05-19
if i remember correctly, sage 4.8 (on ubuntu 12.04) did not  work with libssl1.0.0 but with libssl0.9.8 only. i did not test sage 5.0 with libssl1.0.0 only.

---

### Post by rtalcott on 2012-05-19
I did have  libssl1.0.0 installed but that didn't work for me...I was a bit surprised when I checked...oh well...everything is working well now due to your assistance!

Time to start playing with SAGE!
rt

---

### Post by surfer on 2012-05-19
here are some nice ideas to play with: [projecteuler.net]("https://projecteuler.net/") (although most of them [up to problem 80; that's where is  stand right now] can be solved with plain python).

i have to warn you though... prjecteuler is very addictive!

---

