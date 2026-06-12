---
title: "OpenGL GLX Lubuntu Is using direct rendering but Steam says it is not."
date: 2015-02-11
forum: Gaming &amp; Leisure
---

### Post by Jenopo on 2015-02-11
Freshly installed 14.10 Lubuntu yesterday, Steam installed no problem, after logging in today and installing a game, I found it wouldn't launch.  Every time I open Steam, I get the message that it is not using direct rendering, however after following this: [https://allaboutmynonexistedworld.wordpress.com/2014/06/02/lubuntu-install-opengl/](https://allaboutmynonexistedworld.wordpress.com/2014/06/02/lubuntu-install-opengl/) specifically running the "glxinfo |grep direct" code, it comes up saying "Direct Rendering: yes."   The games now make an attempt to launch but simply crash/don't display. I've recently checked the forums and added the Xorg-enders PPA, but most of this hasn't led anywhere. any help?  Computer is HP envy M6, with a Radeon 8650G graphics card.   Thanks in advance.

---

### Post by R33D3M33R on 2015-02-11
Try this with OSS drivers: [http://askubuntu.com/questions/506349/opengl-glx-context-is-not-using-direct-rendering-which-may-cause-performance-pr/538907#538907](http://askubuntu.com/questions/506349/opengl-glx-context-is-not-using-direct-rendering-which-may-cause-performance-pr/538907#538907)

---

### Post by Jenopo on 2015-02-11
That kind of worked, I got the game going but it then closed itself after the first couple of screens, The OpenGL warning has stopped though, any idea why it would load then stop?

---

### Post by Jenopo on 2015-02-12
Ok, Update, the games are still not launching at all, apart from amnesia which launches and then closes after the initial messages about play. The above fix, posted byR33D3M33R, has got me to this point. Any reasons why it won't run. The OpenGL problem has gone now.

---

### Post by Jenopo on 2015-02-13
Update again: ran a game with the console open, was returned this: > PROBLEM: You appear to have OpenGL 1.4.0, but we need at least 2.0.0!
Could not find required OpenGL entry point 'glGetError'! Either your video card is unsupported, or your OpenGL driver needs to be updated. 

---

### Post by R33D3M33R on 2015-02-13
Can you post the results of:

```
glxinfo | grep "renderer string"
```

?

---

### Post by Jenopo on 2015-02-13
[HR][/HR]Sure```

OpenGL renderer string: Gallium 0.4 on AMD ARUBA

```

---

### Post by R33D3M33R on 2015-02-13
What about the command:
```
glxinfo | grep OpenGL
```

If you don't mind using cutting edge, but maybe unstable, drivers, you could also try adding this PPA: [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

---

### Post by Jenopo on 2015-02-13
This:
```

OpenGL vendor string: X.Org
OpenGL renderer string: Gallium 0.4 on AMD ARUBA
OpenGL core profile version string: 3.3 (Core Profile) Mesa 10.3.2
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
OpenGL version string: 3.0 Mesa 10.3.2
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
OpenGL ES profile version string: OpenGL ES 3.0 Mesa 10.3.2
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.0
OpenGL ES profile extensions:

```

---

### Post by R33D3M33R on 2015-02-13
Everything looks normal from the output.

You can try this: go into the game folder and search for libstdc++ and/or libgcc. Both files end with .so. Remove them from game folder (put them somewhere else) and try to run the game. I advise you to try removing libstdc++ first, if it doesn't work put it back and remove libgcc. If this doesn't work, try to remove both.

---

### Post by Jenopo on 2015-02-13
Only thing matching was not a .so, but a .deb. It came up with permission denied when I tried to move them, but I am using my main (sudo) account.#

EDIT: wait thsi was wrong I found a few of them, but moved some around, to no avail, which specific folder should i take it from?

---

### Post by R33D3M33R on 2015-02-13
Some games seem to come with libraries that are not compatible with the OSS drivers. When you launch the game it first looks in the game folder and if the files are not there, it looks into the system files. These hardcoded game libs could be anywhere in the game folder, so you will have to do some researching. 

You could also try and install the fglrx drivers. You will find them in the packages fglrx-updates-core and fglrx-updates

---

### Post by Jenopo on 2015-02-14
Ok, I'll have a look around. Those packages returned the GLX error message in steam, going to try removing the files again.

---

### Post by greg69 on 2015-02-17
I had this issue as well. It took me a WHOLE lot of messing about to get it fixed. It had been working fine for weeks but then one morning just broke. I got it fixed using a PPA. The whole problem is detailed [http://ubuntuforums.org/showthread.php?t=2262527&p=13215413#post13215413](http://ubuntuforums.org/showthread.php?t=2262527&p=13215413#post13215413) << Here.

---

