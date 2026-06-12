---
title: "supertux svn framerate issue"
date: 2009-04-02
forum: Gaming &amp; Leisure
---

### Post by 2Karl on 2009-04-02
Hi all, I have searched the forums for this issue but have been unable to find it, perhaps someone could help.

I installed Supertux from the repositories (supertux-stable) and it runs nice and smooth, vsynced to my screen refresh of 85Hz on my nvidia 9800 GTX+. (Yes I know it's overkill for the game, but it's not my main reason for playing).

when I downloaded the Supertux developer version (which I believe has a new GL renderer in it), my framerate is capped to 68fps. Not only is it not vsynced, but 68 seems like a very odd number. I've tried switching between sdl and opengl in the config file, but regardless of the renderer it never gets past 68fps.

Investigating further I downloaded the supertux source from SVN and compiled. compilation was fine, but the issue persists. I tried enabling vsync in the supertux config, disabling it, even editing the source to hard code it on and off, no difference, the framerate is always capped at 68fps and the scrolling is slightly jerky.

Has anyone experienced this issue? know a solution?

By the way other openGL apps and games (glxgears, darwinia, nexiuz) work fine and run ant a constant vsynced 85fps. Supertux stays at 68fps whether compiz is enabled or not. It occurs whether windowed or fullscreen.

For the record, I'm really not that interested in playing supertux, but becasue I know that this issue occurs, I feel the need to keep fiddling until it's fixed. I guess that's the curse of the linux user.

Look forward to any help people can give.

Thanks,
Karl.

---

### Post by 2Karl on 2009-04-06
Any suggestions? Am I better off posting directly in the supertux forums?

---

### Post by hessiess on 2009-04-06
Contact the developer(s) ;)

---

