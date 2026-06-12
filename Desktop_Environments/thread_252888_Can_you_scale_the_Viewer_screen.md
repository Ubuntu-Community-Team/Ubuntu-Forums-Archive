---
title: "Can you scale the Viewer screen?"
date: 2006-09-07
forum: Desktop Environments
---

### Post by MetalMusicAddict on 2006-09-07
I have an server with a larger screen than my laptop.

Can I scale the contents of the viewer screen so I can see all of it on a smaller screen? ie: see all of a 1024x768 desktop on a 800x600 screen.

Im using x11vnc on the server and xvncviewer on the desktop.

Ive done this in windows before with RealVNC. Was some kind of "scale" option. I just dont know if the different types of VNCs support the same options. I dont know if its options set on the server or viewer side. I though it was on the viewer side.

PS. I know I could just change th screen size of the server but thats not what Im tryin to do.

---

### Post by krunge on 2006-12-12
Try x11vnc -scale 3/4 ...   (since 800 is about 3/4 of 1024)

---

### Post by MetalMusicAddict on 2006-12-12
Looking more over the [documentation]("http://www.realvnc.com/products/free/3.3.7/man/vncviewer.html") I dont think I can do it.

---

### Post by krunge on 2006-12-14
I'm now not sure what you want to do.  I believe you are correct that the
Unix vncviewer does not do client-side scaling (but I believe at least some
of the Windows viewers do).

However I was suggesting doing server-side scaling:

```
x11vnc -display :0  -scale 3/4
```

that way when you connect with the viewer it will be prescaled to the
size you want.

It is also possible to change the server-side scaling dynamically with
x11vnc by remotecontrol option -R,

```
x11vnc -display :0  -R scale=5/6
```

(this will talk to the running x11vnc and tell it to change the scale,
-R scale=1 would turn off scaling).

---

### Post by MetalMusicAddict on 2006-12-14
Your right. Client-side scaling on linux is what I wanna do. Ill look into your tip though. Thanx.

---

### Post by 8daysaweek.co.uk on 2007-11-09
A reasonably easy solution I've found is to run TighVNC viewer in WINE.  Scaling works as normal :)

---

