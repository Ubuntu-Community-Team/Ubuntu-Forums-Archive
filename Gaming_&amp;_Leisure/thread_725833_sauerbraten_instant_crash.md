---
title: "sauerbraten instant crash"
date: 2008-03-16
forum: Gaming &amp; Leisure
---

### Post by fluxbomber on 2008-03-16
I'm trying to get sauerbraten to run but when i try to run it it instantly crashes this is what i typed in:
```
zachary@zac:~$ chmod +x /home/zachary/Desktop/sauerbraten_unix
chmod: cannot access `/home/zachary/Desktop/sauerbraten_unix': No such file or directory
zachary@zac:~$ cd /home/zachary/Desktop
zachary@zac:~/Desktop$ cd sauerbraten
zachary@zac:~/Desktop/sauerbraten$ chmod +x sauerbraten_unix
zachary@zac:~/Desktop/sauerbraten$ ./sauerbraten_unix
Using home directory: /home/zachary/.sauerbraten
init: sdl
init: enet
init: video: mode
Unable to create OpenGL screen: Couldn't find matching GLX visual

```
any idea whats wrong (or how to fix the " Couldn't find matching GLX visual" problem)?

---

### Post by FrozenFox on 2008-03-16
Erm, are your video drivers installed correctly? Most of the time I ever see a "glx" problem is because of the video drivers. If you don't know, please run glxinfo | grep direct  in the terminal. Direct rendering should indeed be enabled.

---

### Post by fluxbomber on 2008-03-20
i think your right:
```
zachary@zac:~$ glxinfo | grep direct 
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

---

