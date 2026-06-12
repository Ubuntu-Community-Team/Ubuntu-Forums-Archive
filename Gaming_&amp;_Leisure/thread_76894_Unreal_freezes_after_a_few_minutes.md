---
title: "Unreal freezes after a few minutes"
date: 2005-10-15
forum: Gaming &amp; Leisure
---

### Post by detour on 2005-10-15
I'm trying to play Unreal Tournament 2004. I properly installed my video drivers (ATI Radeon 9800 Pro) and the game does run. However, the game always freezes within a few minutes. If I watch the movie that plays after you start a new profile, it freezes near the end. If I skip the movie and start the first round, it freezes within a minute or two of starting the match. I had the game installed with Hoary and played at 1280x1024 resolution. Currently, I've beeen trying to play with the defaults. Any suggestions?


Output that leads me to believe my video is working properly:

$ lspci | grep ATI

0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro]
0000:01:00.1 Display controller: ATI Technologies Inc Radeon R350 [Radeon 9800 Pro] (Secondary)

$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 Pro Generic
OpenGL version string: 1.3.5272 (X4.3.0-8.16.20)

$ glxgears -iacknowledgethatthistoolisnotabenchmark
22163 frames in 5.0 seconds = 4432.579 FPS
22114 frames in 5.0 seconds = 4422.698 FPS
22107 frames in 5.0 seconds = 4421.399 FPS
22115 frames in 5.0 seconds = 4422.974 FPS
22117 frames in 5.0 seconds = 4423.388 FPS

---

### Post by seethru on 2005-10-16
you installed these from the ATI website yes?

Run this
```
$ glxinfo | grep render
```
if you get this back
> direct rendering: No
GLX_ATI_render_texture
OpenGL renderer string: Mesa GLX Indirect

Read this:

[QUOTE=TLE]It's definitely the ATI driver installation that's the problem. This has given a lot of people a lot of problems. The drivers you download from the ATI web-sit doesn't install properly. But as far as I know the solutions posted in the following threads has worked for some people, including me. If you're running the 64 bit version of Ubuntu 5.10 it is somewhat worse, I don't think there's any solution for that, yet. Anyway try and have a look:
[http://www.ubuntuforums.org/showthread.php?t=75378&highlight=mlomker]("http://www.ubuntuforums.org/showthread.php?t=75378&highlight=mlomker")
[http://www.ubuntuforums.org/showthread.php?t=65276&highlight=mlomker]("http://www.ubuntuforums.org/showthread.php?t=65276&highlight=mlomker")
[http://www.ubuntuforums.org/showthread.php?t=76057&highlight=mlomker]("http://www.ubuntuforums.org/showthread.php?t=76057&highlight=mlomker")
[http://www.ubuntuforums.org/showthread.php?t=76116&highlight=mlomker]("http://www.ubuntuforums.org/showthread.php?t=76116&highlight=mlomker")

And if that doesn't do it try and search the forum for "how to ati fglrx"
Good luck[/QUOTE]

---

### Post by detour on 2005-10-16
[QUOTE=seethru]you installed these from the ATI website yes?[/QUOTE]

Thanks for the reply. Actually i installed from the repository, sorry should have mentioned that. This is my output:

$ glxinfo | grep render
direct rendering: Yes
    GLX_ATI_render_texture
OpenGL renderer string: RADEON 9800 Pro Generic

It may be interesting to note that I installed Cedega/Point2Play and successfully played Abe's Oddysee and StarCraft. I'm going to try installing Doom 3 to see if it suffers from the issue as well.

---

