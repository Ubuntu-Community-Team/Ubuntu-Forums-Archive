---
title: "apt-get won't work"
date: 2008-12-02
forum: General Help
---

### Post by yanom on 2008-12-02
when i try to apt-get install something this happens:
```
Setting up libboost-python-dev (1.34.1-11ubuntu1) ...
Traceback (most recent call last):
  File "/usr/bin/pyversions", line 327, in <module>
    main()
  File "/usr/bin/pyversions", line 282, in main
    print default_version(opts.version_only)
  File "/usr/bin/pyversions", line 126, in default_version
    _default_version = link = os.readlink('/usr/bin/python')
OSError: [Errno 22] Invalid argument: '/usr/bin/python'
/usr/share/python/runtime.d/libboost-python-dev.rtupdate unknown python version
dpkg: error processing libboost-python-dev (--configure):
 subprocess post-installation script returned error exit status 1
Setting up libglib1.2ldbl (1.2.10-19build1) ...

Setting up libgtk1.2-common (1.2.10-18.1build2) ...

Setting up libgtk1.2 (1.2.10-18.1build2) ...

Setting up gtkglarea5 (1.2.3-3ubuntu1) ...

Setting up python-visual (3.2.9-4.1) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Errors were encountered while processing:
 libboost-python-dev
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@ubuntu:/home/yanom# 


```


what is going on????

---

### Post by frankleeee on 2008-12-02
Are you doing it in the root terminal, use the regular terminal and  run
sudo apt-get install "package"

---

### Post by m_l17 on 2008-12-03
Using APT:

[https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGetHowto]("https://help.ubuntu.com/community/AptGet/Howto?action=show&redirect=AptGetHowto")

And make sure you don't have Synaptic Package Manager running.

---

### Post by Slim Odds on 2008-12-03
> OSError: [Errno 22] Invalid argument: '/usr/bin/python'Is your python install hosed?

---

### Post by yanom on 2008-12-03
I am doing this in the root terminal, but regular terminal with sudo does the same thing. I am pretty sure my python isn't hosed, and i am doing this with no other applications running. 

Also, most stuff actually installs when i apt-get install it. It just gives a funny error

---

### Post by yanom on 2008-12-05
post just to bump the thread

---

### Post by Slim Odds on 2008-12-05
as I mentioned in the previous post, it's complaining that '/usr/bin/python' is invalid.

It there such a file? Mine is a symbolic link that points to python2.5

---

### Post by yanom on 2008-12-06
I ran this:

```
sudo ln -s -f /usr/bin/python2.5 /usr/bin/python

```

and it stopped giving me funny errors

i think my problem was that /usr/bin/python was a hard link and not a symbolic one. Thanks!!

---

### Post by eternalnewbee on 2008-12-06
> LINUX. IT'S SO EASY, EVEN A PENGUIN CAN DO IT. 
Can a penguin mark his/her thread as solved?:D

---

