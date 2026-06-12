---
title: "python 3.0? Install it or not?"
date: 2008-12-04
forum: General Help
---

### Post by kakyoism on 2008-12-04
Hi

I read that python 3.0 has come out. Is it OK to upgrade right away without breaking anything?

When I apt-get, I only see python3.1, and python3.2 there upon a tab completion. What happened to python3.0???

Thanks!

---

### Post by colsandurz on 2008-12-04
It depends.  I write python programs a lot and you want the new features (link below) then, yes upgrade.  But, if you don't write python code at all and you don't need to use python3 for anything, then wait until it's in the repos.

[http://docs.python.org/dev/3.0/whatsnew/3.0.html](http://docs.python.org/dev/3.0/whatsnew/3.0.html)

Devin

---

### Post by jmauster on 2008-12-06
This is a total newbie question, but how do I get python 3.0 working?

I just installed ubuntu 8.10. I did all the upgrade manager stuff, then I went into synaptic and got the package called python3. 

However, when I'm in the terminal, it still looks like I'm running 2.5.

```
evan@evan-laptop:~$ python
Python 2.5.2 (r252:60911, Oct  5 2008, 19:24:49) 
[GCC 4.3.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.

```

I know I must be missing something really simple and any help would be appreciated.

---

### Post by snova on 2008-12-06
Installing it won't do you much good unless you're a programmer who wants to start writing for the newest version.

Python 3 breaks compatibility, however installation should not affect any applications as they will still use Python 2.x.

The /usr/bin/python symlink doesn't point to Python 3.0, and you would probably be best off not changing it. Run 'python3.0' instead to get the new interpreter.

---

### Post by anjanesh on 2008-12-07
```
user@al-ubuntu:~$ sudo apt-get install python3
python3                 python3.0-ctypes        python3.0-elementtree   python3.0-profiler      python3.2               python3-dbg             python3-gdbm-dbg        python3-tk-dbg
python3.0               python3.0-dbg           python3.0-examples      python3.0-tk            python3-all             python3-dev             python3-minimal         
python3.0-celementtree  python3.0-dev           python3.0-gdbm          python3.0-wsgiref       python3-all-dbg         python3-doc             python3-profiler        
python3.0-cjkcodecs     python3.0-doc           python3.0-minimal       python3.1               python3-all-dev         python3-examples        python3-tk              
user@al-ubuntu:~$ sudo apt-get install python3
```
1. What are python3.1 & python 3.2 ?
2. sudo apt-get install python3-all installs to which directory ?

---

### Post by snova on 2008-12-07
I've never heard of python3.1 or python3.2. They haven't even officially released 3.0 yet!

I think you mean the release candidate? 'python3.0' is RC1. RC2 isn't in the repos yet.

'python3' is supposed to depend on the latest version, so this is probably what you should install.

---

### Post by anjanesh on 2008-12-07
Python 3.0 final was out last week - I was hoping this to be in the repo, not the RCs.

---

### Post by kakyoism on 2008-12-07
I got it.
No 3.0 for Hardy yet. That's why I can't apt-get it.
Thanks folks!

---

### Post by snova on 2008-12-07
> **anjanesh said:**
> Python 3.0 final was out last week - I was hoping this to be in the repo, not the RCs.

Nice! Thanks, I'm going to go build it. :D

kakyoism: If you want the latest version, you'll have to build it from source. It's not difficult. There are instructions contained in the tarball that should work.

---

### Post by TeXtonyx on 2008-12-07
> **snova said:**
> Nice! Thanks, I'm going to go build it. :D

kakyoism: If you want the latest version, you'll have to build it from source. It's not difficult. There are instructions contained in the tarball that should work.


[http://www.python.org/download/](http://www.python.org/download/)
# Python 3.0 compressed source tarball (for Linux, Unix or OS X)
# Python 3.0 bzipped source tarball (for Linux, Unix or OS X, more compressed)

---

