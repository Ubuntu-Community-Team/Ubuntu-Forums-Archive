---
title: "No Desktop Effect"
date: 2011-06-02
forum: Desktop Environments
---

### Post by lhoepfner on 2011-06-02
I just installed Ubuntu 11.04 on my laptop. It was running 10.10 fine before, but did a clean install do avoid any problems.

After restart a couple of times i got a message that was something like 'You do not have hardware to run Unity....' and it then went to fallback mode, or what it is called. This is ok. I can live without Unity, but now when I try to log in to Ubuntu Classic I have no effect at all. It seems like compiz have stopped working entirely.

My graphics card is Radeon x1250 and I use the open source ATI driver. I tried [reinstalling]("https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch") it, but it didn't help. 

When I do 'compiz --replace' I get this in the end:

Compiz (opengl) - Fatal: GLX_EXT_texture_from_pixmap is missing
Compiz (opengl) - Fatal: Software rendering detected

I tried on Google and it seems like it might have something to do with something blocking KMS, but I am absolutely no expert. Also, the laptop cannot shut down anymore without holding the button. It just frezes on a black screen. 

Hope someone can help me out.

---

