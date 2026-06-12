---
title: "Second Life: Window Creation Error"
date: 2007-05-27
forum: Gaming &amp; Leisure
---

### Post by Tarvok on 2007-05-27
I just downloaded and extracted version 1.6.0.6. I get the error "Window creation error" with the following termination text:
```
2007-05-27T03:47:07Z INFO: OSMessageBoxSDL: Creating a dialog because we're in windowed mode and GTK is happy.
2007-05-27T03:48:33Z INFO: Skipping quitCursors: mWindow already gone.
2007-05-27T03:48:33Z INFO: destroyContext begins
2007-05-27T03:48:33Z INFO: destroyContext: shutdownGL begins
2007-05-27T03:48:33Z INFO: destroyContext: SDL_QuitSS/VID begins
2007-05-27T03:48:33Z WARNING: createWindow: LLWindowManager::create() : Error creating window.2007-05-27T03:48:33Z WARNING: LLViewerWindow: Unable to create window, be sure screen is set at 32-bit color and your graphics driver is configured correctly.  See README-linux.txt for furth er information.
2007-05-27T03:48:33Z INFO: remove_marker_file()

```

The first suggestion in the readme is that my card isn't up to specs. It is. It's a Radeon 9800. The second is that fglrx is not properly installed, Well:

```
tarvok@Rider:~/SecondLife_i686_1_16_0_6$ glxinfo |grep direct
direct rendering: Yes
tarvok@Rider:~/SecondLife_i686_1_16_0_6$
```

and...

```
tarvok@Rider:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9200 Series DDR Generic
OpenGL version string: 1.3.1072 (X4.3.0-8.25.18)

tarvok@Rider:~$
```

Of course, it asks me to make sure I'm running in 32 bit color, and I'm not entirely sure how to check that. I'm pretty sure it's in xorg.conf, but I don't know where.

I'd take it to the linux alpha testers forum on the Second Life website, but it doesn't let you access the forums unless you've logged into Second Life at least once, which is kind of hard to do when the client won't even start. (Yes, I have put payment info on file, though, of course, I have not subscribed to a premium account.) Any ideas?

---

### Post by eye208 on 2007-05-29
Your version of fglrx is very old and does not provide OpenGL 2.0 which is required by Second Life.

---

### Post by Tarvok on 2007-06-03
How would I go about fixing this? So far as I know, I'm using the newest version found in Ubuntu's repositories.

---

### Post by viciouslime on 2007-06-03
> **Tarvok said:**
> How would I go about fixing this? So far as I know, I'm using the newest version found in Ubuntu's repositories.

Upgrade to a newer version of Ubuntu :)

---

### Post by Tarvok on 2007-06-07
Oh. So it isn't really sufficient to continue using Dapper (the Long Term Stable). So I guess I'll move on to Feisty, since I am genuinely curious about Second Life.

Is there anything I need to watch out for when I do upgrade?

---

