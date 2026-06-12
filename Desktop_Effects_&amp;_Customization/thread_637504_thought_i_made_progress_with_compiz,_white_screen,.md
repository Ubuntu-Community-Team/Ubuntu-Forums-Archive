---
title: "thought i made progress with compiz, white screen, need help"
date: 2007-12-11
forum: Desktop Effects &amp; Customization
---

### Post by ride1226 on 2007-12-11
after two days of struggle with this unbelievable ati xpress 200 card i am beggining to get very frustrated...however i do make some progress. i found this how to [http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support#](http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support#) and followed it. now when i do compiz --replace or enable anything besides none in effects the windows begin to change and then the screen turns white. after lettin it sit on its white screen it doesnt render...however i know everything is still behind that white screen. i can switch work places back and forth and i know that because the curson in the spot where my aim window is goes away and comes back. so....now im stumped again.

here is the output of glxinfo | grep direct
glxinfo | grep vendor
fglrxinfo

```
milby@milby-laptop:~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
milby@milby-laptop:~$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa project: www.mesa3d.org
milby@milby-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

milby@milby-laptop:~$ 
```

---

### Post by ride1226 on 2007-12-11
bumping this thread in sheer desperateness and hope

---

### Post by gurth4ng on 2007-12-12
i'm stuck on this stupid white screen as well...

/confused

---

### Post by haydnv on 2008-01-13
> **gurth4ng said:**
> i'm stuck on this stupid white screen as well...

/confused

same here (1G macbook pro, i.e. ati restricted driver, with dual-head monitor)

---

### Post by Sef on 2008-01-13
1) What are your systems specs?

2) Have you managed to resolve your problem?

---

### Post by Kilz on 2008-01-14
> **ride1226 said:**
> after two days of struggle with this unbelievable ati xpress 200 card i am beggining to get very frustrated...however i do make some progress. i found this how to [http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support#](http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support#) and followed it. now when i do compiz --replace or enable anything besides none in effects the windows begin to change and then the screen turns white. after lettin it sit on its white screen it doesnt render...however i know everything is still behind that white screen. i can switch work places back and forth and i know that because the curson in the spot where my aim window is goes away and comes back. so....now im stumped again.

here is the output of glxinfo | grep direct
glxinfo | grep vendor
fglrxinfo

```
milby@milby-laptop:~$ glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
OpenGL renderer string: Mesa GLX Indirect
milby@milby-laptop:~$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa project: www.mesa3d.org
milby@milby-laptop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Mesa project: www.mesa3d.org
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.1)

milby@milby-laptop:~$ 
```

The info should be ati. The reason you are getting a white screen is because the driver isnt ati.

---

