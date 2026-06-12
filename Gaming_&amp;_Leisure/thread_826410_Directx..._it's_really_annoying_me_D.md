---
title: "Directx... it's really annoying me D:"
date: 2008-06-11
forum: Gaming &amp; Leisure
---

### Post by kaldor on 2008-06-11
I play games like Quake III and Jedi Knight 3. I can play them on Linux just fine, but the graphics are all messed up because directx won't work for me. 

OpenGL won't work either. Quake III only requires OpenGL... any link for that?

JK3 need directx. Any help on that? >.>

My graphics card is an ATI.

---

### Post by Yuki_Nagato on 2008-06-11
This might not help but,

[http://www.larsen-b.com/Article/231.html]("http://www.larsen-b.com/Article/231.html")

Scroll down the page until you hit the "install mesa" part.

I am guessing these libraries are perhaps not installed?  But be careful, as I have not done this myself.

---

### Post by 4th guy on 2008-06-12
Quake 3 runs naitivly on Linux.
This might be outdated, but it's a good place to start:
[http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3](http://www.linux-gamers.net/modules/wiwimod/index.php?page=HOWTO+Quake3)

---

### Post by cogadh on 2008-06-12
DirectX is a Windows only API developed by Microsoft, there is no way it will ever be available for Linux. The only way to run Windows games on Linux is through Wine, which includes its own implementation of DirectX and is capable of running Jedi Academy perfectly:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=2315](http://appdb.winehq.org/objectManager.php?sClass=version&iId=2315)

OpenGL support is a function of your video card's drivers. As long as you have installed the restricted drivers for your video card, you have OpenGL support. If you haven't installed the restricted drivers, then that is probably why you are missing OpenGL support and may also be why DirectX games run through Wine don't work (Wine translates DirectX API calls into OpenGL calls).

---

### Post by Sleaka J on 2008-06-12
I thought that since Jedi Knight Academy used the Quake 3 engine it ran using OpenGL.

---

### Post by cogadh on 2008-06-12
I honestly don't know, I'm just working off what the OP said. Its entirely possible that JK3 does use OpenGL, but that doesn't mean it doesn't also need DirectX. DX is much more than just a graphics API, which is all that OpenGL is. DX also does sound, input and networking (plus a few other things). Even so, if OpenGL isn't working due to a driver issue, it doesn't really matter what JK3 actually uses, it still won't work.

---

