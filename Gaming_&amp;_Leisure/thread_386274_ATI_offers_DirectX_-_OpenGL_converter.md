---
title: "ATI offers DirectX - OpenGL converter"
date: 2007-03-16
forum: Gaming &amp; Leisure
---

### Post by Josey on 2007-03-16
[http://www.macworld.com/news/2006/11/10/hlsl2glsl/index.php](http://www.macworld.com/news/2006/11/10/hlsl2glsl/index.php)

Will linux gamers benefit from this?

> Graphics chip maker ATI Technologies has released HLSL2GLSL, an open source application designed to help programmers convert graphics code optimized for Windows’ DirectX 9 Application Programming Interface (API) to OpenGL, which is used on the Mac. Binaries for Mac OS X and Windows are available for download.

High Level Shader Language (HLSL) was developed by Microsoft to enable programmers using its DirectX API to develop complex graphical effects. Its OpenGL equivalent is GLSL, and this application enables developers to translate HLSL shaders into GLSL instead. The software generated either GLSL 1.10.58 desktop OpenGL shaders or ES SL v1.00 embedded OpenGL ES shaders.

Many Mac OS X programmers already working on Mac games or cross-platform conversions already have home-rolled tools in their own libraries that provide them with the ability to convert DirectX code into OpenGL code. Commercial products exist that do the same. But ATI is offering this software — released earlier this month as version 0.9 — to further assist programmers who want some help.

The download includes documentation and a library file, along with a standalone command line application that converts snippets of HLSL code into GLSL instead.

---

### Post by Choad on 2007-03-16
nice

---

### Post by Polygon on 2007-03-16
what a name... hlsl2glsl.... lol

im not sure if this will help linux users as  its closed source.... and therefore unless we decompile it (illegal...?) we cant even get a working linux port

---

### Post by Protoss on 2007-03-16
Well this should make it easier for game developers to make their games OpenGL, which will therefore make it much easier to run in linux, even under Wine.

---

### Post by Phenax on 2007-03-16
> **Polygon said:**
> what a name... hlsl2glsl.... lol

im not sure if this will help linux users as  its closed source.... and therefore unless we decompile it (illegal...?) we cant even get a working linux port

Just as the first sentence in that article states, it's open source.

Anyway, as someone who has tinkered with both, I doubt this will push a company towards porting their game. The differences between OpenGL and DirectX aren't massive, and are pretty much just changing the function call and maybe some arguments for the most part.

---

### Post by blanky on 2007-03-16
> 
im not sure if this will help Linux users as its closed source.... and therefore unless we decompile it (illegal...?) we cant even get a working Linux port


Uh...did you read it.

> 
Graphics chip maker ATI Technologies has released HLSL2GLSL, an **open source** application designed to help programmers convert graphics code optimized for Windows’ DirectX 9 Application Programming Interface (API) to OpenGL, which is used on the Mac. Binaries for Mac OS X and Windows are available for download.


This is pretty old news, and it only translates shaders from HLSL to GLSL, not the entire application written in DirectX9 to OpenGL. I can see something like Cedega/Wine benefitting from this though, in regards to rendering shaders from applications that make use of HLSL. (*I think I remember Cedega having a similar technology*)

---

### Post by Polygon on 2007-03-17
my bad :D

it should help a little, but games written natively for opengl still would perform a lot better though... i do hope that it helps wine however.

---

