---
title: "GIMP Help..."
date: 2006-10-02
forum: Desktop Environments
---

### Post by misterE0 on 2006-10-02
Can anyone point me in the right direction?  I've got one prog that's keeping me from wiping windows completely...we all know already what it is.  Photoshop.  I've been trying to work with the gimp instead, I do a lot of mild photo editing (mostly product photos shot in a diffusing tent).  I am a semi-pro photographer and need to learn this tool better.  What I do is mostly just removing the background from an image.  The background is mostly white (but there may be visible wrinkles in the cloth).

In photoshop, I simply grab the wand click around a few times, hit delete, and voila.  The only time i have to work harder is when the edges of an object are not very much in contrast to the background, things made of metal usually.  So in the gimp, there is a similar tool, but it works nothing like the photoshop sibling.  Anyone have any suggestions?  I'd love to learn enough to make the gimp as useful as photoshop is to me.

P.S.  I've installed pixel, but it doesn't seem to run correctly (probably because of compiz) but I'm not going to fight with it until it's more mature.

---

### Post by orb9220 on 2006-10-02
[http://docs.gimp.org/en/gimp-tool-fuzzy-select.html](http://docs.gimp.org/en/gimp-tool-fuzzy-select.html)
[http://www.ischool.utexas.edu/technology/tutorials/graphics/gimp/04_selections/05_color.html](http://www.ischool.utexas.edu/technology/tutorials/graphics/gimp/04_selections/05_color.html)

Don't know about this message.

> > : I'm using the last debian version of gimp. Circle 
> : selection works fine with antialiasing - when I make 
> : a selection and move it, the borders of selected 
> : area are antialiased. When I repeat the same process 
> : with "magic wand" (fuzzy selection), the borders are 
> : always sharp - not antialiased (doesn't respect antialiasing 
> : choise of fuzzy selection tool).
> : 
> : Any ideas?
> 
> I thought I'd check this out, but I am not sure what the anti-alias 
> function is supposed to do in the Magic Wand tool. Could somebody 
> fill me in? Thanks,

that's very ease to try. Just take some photo, select an area with
the fuzzy-select tool, hit Ctrl-C, Ctrl-V and make the new floating
selection a new layer (probably moving it away a bit). Then repeat
that with Antialiasing turned off. Now fill your image with black
so you get a homogenous background to view the differences in the
two layers you have just created.

[http://wiki.freegeek.org/index.php/The_Gimp](http://wiki.freegeek.org/index.php/The_Gimp)

Don't know if any of this will help. But I wanted to give it a try.

---

