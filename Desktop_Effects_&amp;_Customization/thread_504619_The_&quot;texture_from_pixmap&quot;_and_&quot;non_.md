---
title: "The &quot;texture_from_pixmap&quot; and &quot;non power of two textures&quot; problems.."
date: 2007-07-19
forum: Desktop Effects &amp; Customization
---

### Post by fjoesne on 2007-07-19
I have seen a few of posts like these now.. but all of them remain unanswered
> **jtraub said:**
> I have ATi X1900 XT and proprietary drivers installed on my machine (default from Feisty repositories)
```

mikv@hawk:~$ glxinfo | grep rendering
direct rendering: Yes
mikv@hawk:~$ glxinfo | grep texture_from_pixmap
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 

```
But last step of this guide ends with following errors
```

mikv@hawk:~$ compiz --replace
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

```

Any ideas?

have seen a few of posts like these now.. but all of them remain unanswered. So I hope that i get some answers when i make this thread for this sole problem. I have somewhat a similar issue, the difference being that I also get this message:
```
Checks indicate compiz should work on your system
...
...
/usr/bin/compiz.real (core) - Fatal: Support for non power of two textures missing
```

I am running XGL because of ATI's useless and way to late drivers. 3D works pretty well so xgl is functional for now, its just that compiz wont recognize it as functional :/

---

### Post by raul_ on 2007-07-28
BUMP (about that texture_from_pixmap thing) i'm using a intel 950

---

### Post by doragasu on 2007-08-10
I'm having the same problem, I have installed Ubuntu 7.04-amd64-desktop and my graphics card is a Radeon 9600 Pro. ¿Isn't this problem fixed yet?

---

### Post by JockeTF on 2007-08-10
Try this, it works for me while using the dual-head feature on my Intel 945GM.
```
LIBGL_ALWAYS_INDIRECT=1 compiz --replace
```

I got the idea from [_this_](http://ubuntuforums.org/showthread.php?t=519365) thread.

// JockeTF :mrgreen:

---

### Post by doragasu on 2007-08-11
Thanks for help, but it doesn't work for me, I get the same error message.

---

### Post by mrwasabi on 2007-08-12
I'm having a similar issue after installing Beryl on my Sempron system running the ATI X850XT video card, I get this when running **glxinfo | grep texture_from_pixmap:**

 GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method,

However when I run:  **LIBGL_ALWAYS_INDIRECT=1 compiz --replace**

I get this output:

Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.

I'm using the restricted driver manager for my video card and have had no issues until trying to install Beryl, my desktop is stable it isn't crashing or anything. I did notice that the howtoforge website listed several KNOWN working cards, mine however fell into the "Experimental 3D" category. Any ideas?

---

### Post by ricardoec on 2007-09-15
It would be interesting to know where this message comes from. Dos it com from Compiz code, or the Ati drivers. A lot of people have the same issue but nobody seems to understand what is happening.

I also have the message on an ATI x1600 256 MB video ram.

---

