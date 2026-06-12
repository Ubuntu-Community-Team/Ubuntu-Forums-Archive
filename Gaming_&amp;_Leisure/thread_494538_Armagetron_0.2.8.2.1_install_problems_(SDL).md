---
title: "Armagetron 0.2.8.2.1 install problems (SDL)"
date: 2007-07-07
forum: Gaming &amp; Leisure
---

### Post by Mike7171 on 2007-07-07
So I'm installing this through Terminal. (./configure, make, make install). The only problem is that during the configure step, it told me I needed "SDL_IMG", or what ever it was called. So I downloaded it and installed the same way as I was doing with Armagetron. Now, in ./configure, it says this: 

> configure: WARNING: SDL_image header not found where it should be ( the SDL include directory ).

After that it moves on however. I chose to ignore it and continue with the installation. After it was done I tried to run it with "armagetronad -window", but it told me this:

> armagetronad: error while loading shared libraries: libSDL_image-1.2.so.0: cannot open shared object file: No such file or directory

So I think it means SDL_image is not in the right place. Does anyone know how to fix this? 

Thanks,
Mike

---

### Post by KIAaze on 2007-07-09
Are you sure you've installed **libsdl-image1.2** and **libsdl-image1.2-dev** ?
They can be installed through Synaptic package manager. (armagetron too by the way ;) )

libSDL_image-1.2.so.0 should probably be in /usr/lib.
The SDL_image header should be here: /usr/include/SDL/SDL_image.h

If one of them isn't there, it means something went wrong with the installation.

---

### Post by Mike7171 on 2007-07-09
It's all good, I just installed it into Wine and everything is alright lol. It was alot easier.

---

### Post by KIAaze on 2007-07-09
Into Wine?!
Isn't it a GNU/Linux native game?
It certainly is on my PC.

---

### Post by Mike7171 on 2007-07-09
I downloaded the newest version for windows off of the Armagetron site.

---

