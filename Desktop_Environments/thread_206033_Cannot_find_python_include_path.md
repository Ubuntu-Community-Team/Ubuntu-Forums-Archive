---
title: "Cannot find python include path"
date: 2006-06-29
forum: Desktop Environments
---

### Post by buckets on 2006-06-29
I am trying to configure adesklet and am getting an error finding the include path for pything

...
checking for python extension module directory... ${exec_prefix}/lib/python2.4/site-packages
checking for Python include path... find: /usr/include/python/: No such file or directory

configure: error: cannot find Python include path


can anyone tell me what this path is for and how do i fix this problem
Thanks

---

### Post by tonyr on 2006-06-29
The path is for **python** header files (files ending in .h).  The desklet you
are building apparently wants these files.  They are contained in the
package **python2.4-dev**, which is not installed by default.   You
would need to install it with **Synaptic** (or **Adept** if you are using Kubuntu/KDE).

Unfortunately, it does not install the directory  as **/usr/include/python**, but as
**/usr/include/python2.4**.  There may be a command line option for **configure**,
to specify the path  (read the file, there should be some comments in there
about it), or you could edit **configure** directly to change the path
name, or you could make a link in **/usr/include** to satisfy the requirement:

In a terminal
```

sudo ln -s /usr/include/python2.4 /usr/include/python

```

I suspect that since the configure file expects **/usr/include/python** to exist,
there may be other path name failures, too.

---

### Post by buckets on 2006-06-29
thanks that helped.

---

### Post by copey02 on 2006-06-29
i'm having the same problem. i got past the python error and ran into this error:

configure: error: Could not find terminal management library for readline
(either ncurses, termcap or curses).


i tried going into synaptic and installing ncurses, i still get this error. any idea?

---

### Post by dennis1200 on 2007-01-22
you need to install the "-dev" companions to stuff when compiling. I found a helpful french website on the topic (should be on this post as well):

```
sudo apt-get install python2.4-dev libncurses5-dev libreadline5-dev libimlib2 libimlib2-dev xlibs-dev build-essential
```

Then you should be set.

---

### Post by Steve H on 2007-04-26
I´m trying to install adesklets, but when using synaptic or apt-get, i get the following error:

> The following packages have unmet dependencies:
adesklets: Depends: python (< 2.5) but 2.5.1~rc1-0ubuntu3 is installed.  

When I try and install the latest package from the website, after I ./configure i get this error:

> checking for a BSD-compatible install... /usr/bin/install -c
checking for a Python interpreter with version >= 2.3... python
checking for python... /usr/bin/python
checking for python version... 2.5
checking for python platform... linux2
checking for python script directory... ${prefix}/lib/python2.5/site-packages
checking for python extension module directory... ${exec_prefix}/lib/python2.5/site-packages
checking for Python include path... 
configure: error: cannot find Python include path  

So how would I remedy my situation with the symlink? 

I have tried doing it the way showed above but that didn't help.

I even tried:

```
sudo apt-get install python2.4-dev libncurses5-dev libreadline5-dev libimlib2 libimlib2-dev xlibs-dev build-essential
```

But that didn't work and just returned the same dependencies error......

---

### Post by Steve H on 2007-04-27
I did get this message to disappear after using Synaptic to download python-all and python-all-dev with all it's dependencies. I was just getting other error after that concerning GTK. But after trying everything, and installing reinstalling and down right breaking all parts of python.......I gave up and did a fresh install of Feisty. It was just easier in the end.

Everything works beautifully now.

:) 

HOO----RAY!!

---

### Post by coldstatue on 2007-05-01
nevermind

---

