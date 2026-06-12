---
title: "Trying To Install LXQt"
date: 2017-02-27
forum: Desktop Environments
---

### Post by shane_faulkinbury2 on 2017-02-27
I'm trying to install LXQt desktop enviroment to Ubuntu 16.04.  I've downloaded and moved the entire folder to /usr as the how-to states however now I'm having trouble.  I do not see the install file in any of the folders as stated here.

```
To build only CMake and Qt5Core are needed, optionally Git to pull VCS checkouts. Runtime dependencies do not exist.   

Code configuration is handled by CMake. CMake variable `CMAKE_INSTALL_PREFIX` has to be set to `/usr` on most operating systems.   

To build run `make`, to install `make install` which accepts variable `DESTDIR` as usual. (Strictly speaking `make` isn't even needed right now. On the other hand it doesn't hurt so packagers may just include it in case it'll be needed one day.
```

Can someone please help me out?

---

### Post by vasa1 on 2017-02-27
> **shane_faulkinbury2 said:**
> ...

Can someone please help me out?
LXQt, in its present state, is targeted at testers and developers.

---

### Post by shane_faulkinbury2 on 2017-02-27
Oh, so I can't install it then?  Damn  ](*,)

---

### Post by oldos2er on 2017-02-27
Why not install the version in the repositories?

---

### Post by shane_faulkinbury2 on 2017-02-27
Well I installed the [COLOR=#000000]repository[/COLOR], but I'm heading to bed so I'll report back tomorrow night!

---

### Post by shane_faulkinbury2 on 2017-02-28
Well for some reason it didn't work, but I have plenty of more desktop enviroments to try out.  :)

---

### Post by oldos2er on 2017-02-28
Since you've posted no solution to your problem, it's a bit disingenuous to mark your thread 'Solved.' The main purpose in doing that is to assist others who might have the same question; so I'll "unsolve" the thread for you.

 To truly solve your problem we'll need to know what exactly didn't work; any error messages would help.

And btw, lxqt isn't a theme, it's a desktop environment.

---

### Post by shane_faulkinbury2 on 2017-02-28
Sorry about marking the thread as solved [COLOR=#000000]oldos2er, but I'm just going to move on.  I marked the thread as solved because I'm doing so, but sorry I didn't think about anyone else![/COLOR]

---

### Post by jbicha on 2017-03-03
> **vasa1 said:**
> LXQt, in its present state, is targeted at testers and developers.

I've been told that lxqt is better suited for use in 17.04 or 17.10. I've never used lxqt.

(Note that Ubuntu 17.04 is not released yet.)

---

