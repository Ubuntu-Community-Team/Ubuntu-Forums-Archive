---
title: "does counter strike source require open gl"
date: 2007-07-23
forum: Gaming &amp; Leisure
---

### Post by jacob01 on 2007-07-23
i have found that my graphics (intel gma x3000) has open gl 1.5 support and currently i think i have open gl version 1.4 drivers would this cause counter strike source to freeze op while loading. also when i try to play beguled through the steam i get a window but with nothing in it would this be an opengl

what open gl does counter strike source require for opengl?

---

### Post by Myzrael on 2007-07-23
Counter Strike doesn't use Open GL. It uses DirectX.

---

### Post by jacob01 on 2007-07-23
yea it must the source engine was built off opengl

---

### Post by jacob01 on 2007-07-23
what would cause css to frees when trying to load the menu

---

### Post by cogadh on 2007-07-23
Source is not built on OpenGL, it is a DX9-based rendering engine:
[http://developer.valvesoftware.com/wiki/Source_Engine_Features#Renderer](http://developer.valvesoftware.com/wiki/Source_Engine_Features#Renderer)
It supposedly has OpenGL support added in the Playstation 3 version of the engine, but otherwise it is strictly DirectX.

As for what could cause your freeze, there are any number of reasons why it would happen. Have you already reviewed the configuration guide on Wine's AppDB page for the game:
[http://appdb.winehq.org/appview.php?iVersionId=3731](http://appdb.winehq.org/appview.php?iVersionId=3731)

---

### Post by jacob01 on 2007-07-23
thank for replying and yes i have been having this proplen for a month and no one has really attempted to help me but thanks for the help i will try it

---

### Post by jacob01 on 2007-07-23
how do i know what directx level i have

---

### Post by jacob01 on 2007-07-23
because that might be my problem not having the correct direct x

---

### Post by cogadh on 2007-07-23
Wine supports up to DirectX 9.0c by default, although there are a few bugs in it. Counter Strike will set an appropriate DX level based on your hardware. If your hardware is not fully DX 9 compliant, it will set the DX level to 8.

---

### Post by jacob01 on 2007-07-23
ok thanks but i was reating a thread where you can make sure it uses a specific dxlevel by using a terminal and starting up counter strik and add -dxlevel XX
the xx is the level
what is that, would it work

also would that fix my problem were when i launch counterstrike and it freezes at when loading menu

if not do you know what would


thanks for replying

---

### Post by jacob01 on 2007-07-23
do you have to down load directx levels or are they built into the game or wine

---

### Post by cogadh on 2007-07-23
As I said, DirectX is part of Wine, it already supports up to DX 9.0c, you don't need to download anything extra. You can try the "-dxlevel xx" command line option, I think that Intel GPU can do DX 9, so it won't cause any additional problems to try it. The AppDB link I posted earlier gives you instructions on how to use that option.

---

### Post by ||Console|| on 2007-11-05
I have wine installed but steam tells my my GFC card doesnt meet the min req's cause it doesnt haev direct3d Hall ?

---

