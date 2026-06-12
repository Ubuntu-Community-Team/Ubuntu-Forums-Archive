---
title: "ATI released OpenGL-Converter for DirectX-Shader"
date: 2006-11-14
forum: Gaming &amp; Leisure
---

### Post by ubu-for on 2006-11-14
[http://www.heise.de/newsticker/meldung/80946](http://www.heise.de/newsticker/meldung/80946)

> 
heise.de 13. November 2006

ATI veröffentlicht OpenGL-Konverter für DirectX-Shader

Das Tool HLSL2GLSL von ATI übersetzt für Direct3D geschriebene Shader-Programme in ihr OpenGL-Äquivalent und setzt Mac OS X voraus. Die GLSL-Versionen sind dann beispielsweise auf einem Mac-System einsetzbar.

Das Tool verarbeitet HLSL Shader bis zum Shader Model 3.0 und erzeugt GLSL v1.10.59 Desktop OpenGL Shader oder ES SL v1.00 embedded OpenGL ES Shaders. Es steht sowohl in einer Kommando-Zeilen-Version als auch als DLL (mit Source-Code) zur Verfügung, die Entwickler in eigene Applikationen einbinden können. Die Software ist als Freeware unter BSD-Lizenz auf SourceForge.net oder bei Apple erhältlich.


[http://www.macworld.com/news/2006/11/10/hlsl2glsl/index.php](http://www.macworld.com/news/2006/11/10/hlsl2glsl/index.php)

> 
Macworld.com November 10, 2006

ATI offers DirectX - OpenGL converter

By Peter Cohen

Graphics chip maker ATI Technologies has released HLSL2GLSL, an open source application designed to help programmers convert graphics code optimized for Windows’ DirectX 9 Application Programming Interface (API) to OpenGL, which is used on the Mac. Binaries for Mac OS X and Windows are available for download.

High Level Shader Language (HLSL) was developed by Microsoft to enable programmers using its DirectX API to develop complex graphical effects. Its OpenGL equivalent is GLSL, and this application enables developers to translate HLSL shaders into GLSL instead. The software generated either GLSL 1.10.58 desktop OpenGL shaders or ES SL v1.00 embedded OpenGL ES shaders.

Many Mac OS X programmers already working on Mac games or cross-platform conversions already have home-rolled tools in their own libraries that provide them with the ability to convert DirectX code into OpenGL code. Commercial products exist that do the same. But ATI is offering this software — released earlier this month as version 0.9 — to further assist programmers who want some help.

The download includes documentation and a library file, along with a standalone command line application that converts snippets of HLSL code into GLSL instead.


[http://sourceforge.net/projects/hlsl2glsl/](http://sourceforge.net/projects/hlsl2glsl/)

---

### Post by MaximB on 2006-11-14
do you have this in english ?

---

### Post by edemark on 2006-11-14
sorry though i know i should i do not speak german please can i have some more details in inglish. I would also ask, but only because of my small knowledge, that whay it would be useful for me? I have a radeon 345m igp would it help in making its performance better?

thanks

---

### Post by ubu-for on 2006-11-14
> **MAXDDARK said:**
> do you have this in english ?

> **edemark said:**
> sorry though i know i should i do not speak german please can i have some more details in inglish.

I'm sorry, but I couldn't find this news in english anywhere else. [first post updated]

> **edemark said:**
> I would also ask, but only because of my small knowledge, that whay it would be useful for me? I have a radeon 345m igp would it help in making its performance better?

thanks

No. But this tool from ATI makes it easier to port DirectX games (Windows) to OpenGL (MacOS, Linux and Windows). :-)

Similar to this FAKE news:
[http://www.linux-gamers.net/modules/news/article.php?storyid=1197](http://www.linux-gamers.net/modules/news/article.php?storyid=1197)

---

### Post by leech on 2006-11-14
From what someone on OSNews.com was saying, this basically is just for the SHADERS.  Which (according to the poster) are actually pretty simple to convert, since there aren't that many differences between the shaders for DirectX or OpenGL.  All the other stuff that DirectX does though still isn't converted.  All the DirectInput, DirectSound, etc.  

Of course I'm not a programmer, so this could be a huge thing.

Leech

---

### Post by ubu-for on 2006-11-14
> **leech said:**
> From what someone on OSNews.com was saying, this basically is just for the SHADERS.  Which (according to the poster) are actually pretty simple to convert, since there aren't that many differences between the shaders for DirectX or OpenGL.

That's true! But a good start!

> **leech said:**
> All the other stuff that DirectX does though still isn't converted.  All the DirectInput, DirectSound, etc.

Maybe OpenAL could become the new standard for Windows Vista games instead of MS' DirectSound!

> 
... With Microsoft's decision to remove the audio hardware layer in Windows Vista, legacy DirectSound 3D games will no longer use hardware 3D algorithms for audio spatialization. Instead they will have to rely upon the new Microsoft software mixer that is built into Windows Vista. This new software mixer will give the users basic audio support for their old Direct Sound games but since it has no hardware layer, all EAX® effects will be lost, and no individual per-voice processing can be performed using dedicated hardware processing. ...

[http://www.openal.org/openal_vista.html](http://www.openal.org/openal_vista.html)

---

### Post by sthompson on 2007-05-03
> **MaximB said:**
> do you have this in english ?

**(German to English)**

ATI publishes OpenGL converters for DirectX Shader

The Tool HLSL2GLSL translated of ATI for Direct3D written
Shader programs into their OpenGL equivalent and presupposes Mac OS X.
The GLSL versions are then for example applicable on a Mac system.

The Tool processes HLSL Shader up to the Shader Model 3,0 and produces
GLSL v1.10.59 Desktop OpenGL Shader or IT SL v1.00 embedded OpenGL IT
Shaders. It is both in a command line version and and to DLL (with
SOURCE code) at the disposal, which developers can merge into own
applications. The software is available as Freeware under BSD license on
SourceForge.net or with Apple.

---

### Post by scotty2hott2k on 2007-05-03
its useless to us tbh. its for developers developing software which uses directx shaders to convert the source code of their shaders into the opengl shader language.

---

