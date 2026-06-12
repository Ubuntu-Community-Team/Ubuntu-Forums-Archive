---
title: "Game development, OpenGL and DirectX.."
date: 2009-10-26
forum: Gaming &amp; Leisure
---

### Post by billdotson on 2009-10-26
I have heard that DirectX is a bit easier to use and that instead of having DirectX for sound, and another directx thing for video, etc. everything is included. With OpenGL you need OpenAL for sound and now, OpenCL for the GPGPU stuff (DirectX 11 "Compute" is the equivalent I believe).

Anyway, that begs the question, why do game developers make games using DirectX, something that only Windows systems can use? If they are concerned about making money on PC games (which "they" say is part of the reason the focus is shifting to the consoles :-(, apart from piracy ) wouldn't it be more economical to make games with OpenGL and then  make installers for Windows, OS X and Linux (and I assume it would work on BSD as well)? That way developers wouldn't have Linux or OS X users hanging on to Windows just for games (more money for them to buy games with) and there would be (potentially) more money coming in. Could OpenGL, etc. really be that much more difficult, enough to warrant locking it into one operating system forever?

I am starting to work on my own little PC games, and although I am not going to be doing anything that is going to be used in a commercial game (unless you are part of a team there is no way you would ever finish a polished, modern game by yourself) I still couldn't see myself making it so that only Windows systems would run it. That just seems like you are selling your customers/players short.

I haven't done any work with either API yet (I am a noob learning how to do the basics with python) so please enlighten me on the differences and advantages/disadvantages of the two. Does OpenGL stuff make better use of hardware (not need the absolute newest thing) like Linux does with older computers (might be a poor analogy but oh well)?

---

### Post by Vadi on 2009-10-26
Mentality, managers, etc...

No real technical reason not to do otherwise.

---

### Post by Simian Man on 2009-10-26
The fact is that Windows is the PC platform for games.  I know many Linux & Mac users who are also gamers and all of them dual-boot or keep a separate Windows machine for games.  It's just not feasible to be seriously into games on any other system.  Because of this there is very, very little benefit for game companies to distribute games for Linux or Mac.

It isn't even that much a question of OpenGL vs. DirectX since games that target consoles will have to abstract away their rendering code and support multiple platforms anyway - there is no DirectX on the PS3 or Wii, and the one for the Xbox is not exactly the same as the PC one.

It's mostly just that adding the overhead of building, testing, and supporting a game on another platform isn't worth it when few people will buy your game on Linux anyway (and of those who do, most would be able to buy it for another system anyway).

---

### Post by Sindwiller on 2009-10-26
> Could OpenGL, etc. really be that much more difficult, enough to warrant locking it into one operating system forever?

Actually, OpenGL is slightly less painful to use, at least as far as I know.

I think the main advantage people would have from using OpenGL is that they aren't bound to use certain extensions and some functionality only on current-gen hardware (eg. DX10, DX11) and "current-gen" operating systems, meaning those who have been defined by the chip manufacturer or OS vendor as such. In detail, this means that you can still use geometry shaders and other advanced shader functions on Windows XP for example, even though DirectX 10 & 11 (and with that, the use of more complex shader functions in HLSL) is reserved for Vista and Windows 7. Even more so, if your GPU half-way supports a GL extension, it may use it, obviously to some extend. With DirectX, it's either the bits match fully or nada. I can imagine hardware vendors and Microsoft baiting middleware and game developers to use DirectX with additional API information, speed enhancement routines or even money.

But even though OpenGL is practically platform-independent, and there are many libraries who help to bridge the remaining platform differences (GLUT, SDL, etc.), platform-specific libraries and stuff like multi-threading, file management, library handling, sound architecture, etc. can be a big obstacle to port stuff over to another OS.

That being said; it's also good to know that DirectSound and all the other DirectX libraries are more limited than most of their full-fledged, third party contestants. Even more so: Full hardware acceleration and 3d sound in DirectSound has been droppen in Vista and 7 (since it's just Vista with a new toolbar), making OpenAL (and Fmod) much more important for that task.

But what the hell do I know. Learn Python, it's good for you :)

---

