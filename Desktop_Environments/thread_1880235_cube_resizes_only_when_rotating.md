---
title: "cube resizes only when rotating"
date: 2011-11-13
forum: Desktop Environments
---

### Post by esagherardo on 2011-11-13
New to compiz-fusion (am an old no-gui, command-line chap).
Everything works fine (rotation, distension, switch) but one only thing: when I press Ctrl-Alt the cube is active (I can rotate it, while rotating I see very little of the skydome, I can make it zoom while rotating), but not resized; I do not see it floating in the space. I do not see any effect until I start rotation or distension. It seems that the foreface of the cube has exactly the same size of the screen, so it occupy all the screen and hides the skydome. Any hint? 

I have a fully updated lucid lynx on a Toshiba Laptop Satellite Pro. glxgears reports:

```

$ glxgears -info
GL_RENDERER   = Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20091221 2009Q4 
GL_VERSION    = 2.1 Mesa 7.7.1
GL_VENDOR     = Tungsten Graphics, Inc

```

---

### Post by esagherardo on 2011-12-21
Nobody can help me?

> **esagherardo said:**
> New to compiz-fusion (am an old no-gui, command-line chap).
Everything works fine (rotation, distension, switch) but one only thing: when I press Ctrl-Alt the cube is active (I can rotate it, while rotating I see very little of the skydome, I can make it zoom while rotating), but not resized; I do not see it floating in the space. I do not see any effect until I start rotation or distension. It seems that the foreface of the cube has exactly the same size of the screen, so it occupy all the screen and hides the skydome. Any hint? 

I have a fully updated lucid lynx on a Toshiba Laptop Satellite Pro. glxgears reports:

```

$ glxgears -info
GL_RENDERER   = Mesa DRI Mobile Intel® GM45 Express Chipset GEM 20091221 2009Q4 
GL_VERSION    = 2.1 Mesa 7.7.1
GL_VENDOR     = Tungsten Graphics, Inc

```

---

### Post by wildmanne39 on 2011-12-21
Hi, it only gets smaller if you hold down the mouse wheel to turn the cube and have a couple of windows open or use ctrl+alt+left mouse button held down.

I believe this can be changed but I like mine the way it is so I only adjust the size of the cube to zoom out too and I have never tried to make it zoom without windows open.
Thanks

---

### Post by esagherardo on 2012-01-03
> **wildmanne39 said:**
> Hi, it only gets smaller if you hold down the mouse wheel to turn the cube and have a couple of windows open or use ctrl+alt+left mouse button held down.

THANKS. Ok I feel a bit ashamed, but in case someone else dumb as I am will look for this post, I tell the truth: I only use the touchpad... I did not realise that the expected  behaviour only is available when using the wheel of the mouse. Actually I was convinced that pressing the wheel was equivalent to to the fake third button of the mouse (press both).

---

### Post by CMXILies on 2012-01-03
Is there not some way to define your third touchpad button as the mouse wheel? I would bet there is, but don't have a touchpad of my own.

---

### Post by esagherardo on 2012-01-03
> **CMXILies said:**
> Is there not some way to define your third touchpad button as the mouse wheel? I would bet there is, but don't have a touchpad of my own.

Well I have a mouse with the wheel, which I never use. With it everything works fine.

The touchpad is a two buttons mouse, with the standard emulation of third button obtained by pressing the two buttons at once. Apparently the emulation is not complete, since the behaviour is different than with the wheel...

---

### Post by wildmanne39 on 2012-01-03
Hi, I have no idea about the touchpad either but you should use thread tools to mark this thread as solved and if you want to know if you can make it work with a touchpad start as new thread with that as the title that way you can get answers to that exact question.
Thanks

---

### Post by esagherardo on 2012-01-06
You are right. Done. Just to leave complete information in this thread, I found the solution of the "touchpad issue". 

The touchpad may have a scroll wheel built in, even if there is nothing printed/carved on it. I
> 
On the touchpad if you graze up and down the very, very right edge that is the scroll wheel 
  
from [http://forum.notebookreview.com/dell/162659-anyway-emulate-scroll-wheel-touchpad.html#post2396853](http://forum.notebookreview.com/dell/162659-anyway-emulate-scroll-wheel-touchpad.html#post2396853)


Indeed it "works": if with one hand you press both mouse buttons and with the other you graze so to activate the wheel, then you may move on the whole touchpad (while keeping contact with it) and see the cube floating. Of course it's useless, unless you like distorsionism... ;-)

---

