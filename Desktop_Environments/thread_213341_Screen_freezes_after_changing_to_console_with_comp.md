---
title: "Screen freezes after changing to console with compiz"
date: 2006-07-11
forum: Desktop Environments
---

### Post by matj654 on 2006-07-11
I have noticed something strange with compiz: If I try to change to a console screen using CTRL+ALT+F1, and then I switch back to the graphics mode with CTRL+ALT+F7, the screen freezes. This apperas to happen only with compiz, if I try it with metacity it works perfectly.

Once it freezes I can access my computer from another one using telnet, and if I kill the "Xorg-air" (I use airglx with compiz) the X server restarts and i can use my computer once again. But it kills the previous session.

Does anyone have the same problem? 

Thanks.

---

### Post by sethmahoney on 2006-07-11
I do.  Could you post the contents of /etc/X11/xorg.conf ?

---

### Post by crazy___cow on 2006-07-12
I have the same problem too with aiglx/compiz on i915!

---

### Post by matj654 on 2006-07-20
Here you go. I also have a Intel i915 card. 

Also, some days ago, after upgrading compiz the cube rotates very sluggishly. Up until now the movement was perfect, very soft. Have any of you with a i915 card the same problem? Thanks again.

---

### Post by KingCharles on 2007-08-19
Using Feisty, nvidia drivers (from their site), and beryl from standard repos.
Have the same issue. I think this is related to the [framebuffer,]("http://en.wikipedia.org/wiki/Framebuffer") but I could be wrong ;]

<-- EDIT -->
Oh wait... looky here... :)
[http://ubuntuforums.org/showthread.php?t=413903&highlight=switching+between+beryl+console](http://ubuntuforums.org/showthread.php?t=413903&highlight=switching+between+beryl+console)

[SOLVED]

---

