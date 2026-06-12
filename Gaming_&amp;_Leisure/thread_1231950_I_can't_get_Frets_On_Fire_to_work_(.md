---
title: "I can't get Frets On Fire to work :("
date: 2009-08-05
forum: Gaming &amp; Leisure
---

### Post by Emma &lt;3 on 2009-08-05
[B]When I try to play Frets On Fire, it loads up a black screen for a few seconds before vanishing.

I read somewhere that someone used:[/B]

*pasuspender fretsonfire*

**in the terminal.. So I tried it:**

[I]emma-PC emma # pasuspender fretsonfire
/usr/share/games/fretsonfire/game/Song.py:31: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import sha
Traceback (most recent call last):
  File "./FretsOnFire.py", line 69, in <module>
    menu   = MainMenu(engine, songName = songName)
  File "/usr/share/games/fretsonfire/game/MainMenu.py", line 47, in __init__
    self.engine.loadSvgDrawing(self, "background", "keyboard.svg")
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 312, in loadSvgDrawing
    return self.data.loadSvgDrawing(target, name, fileName, textureSize)
  File "/usr/share/games/fretsonfire/game/Data.py", line 106, in loadSvgDrawing
    drawing  = self.resource.load(target, name, lambda: SvgDrawing(self.svg, fileName), synch = True)
  File "/usr/share/games/fretsonfire/game/Resource.py", line 157, in load
    return l.finish()
  File "/usr/share/games/fretsonfire/game/Resource.py", line 68, in load
    self.result = self.function()
  File "/usr/share/games/fretsonfire/game/Data.py", line 106, in <lambda>
    drawing  = self.resource.load(target, name, lambda: SvgDrawing(self.svg, fileName), synch = True)
  File "/usr/share/games/fretsonfire/game/Svg.py", line 544, in __init__
    self.texture = Texture(bitmapFile)
  File "/usr/share/games/fretsonfire/game/Texture.py", line 202, in __init__
    self.loadFile(name)
  File "/usr/share/games/fretsonfire/game/Texture.py", line 206, in loadFile
    self.loadImage(Image.open(name))
  File "/usr/share/games/fretsonfire/game/Texture.py", line 214, in loadImage
    self.loadRaw(image.size, string, GL_RGBA, 4)
  File "/usr/share/games/fretsonfire/game/Texture.py", line 299, in loadRaw
    gluBuild2DMipmaps(self.glTarget, components, w, h, format, GL_UNSIGNED_BYTE, string)
  File "/usr/lib/python2.6/dist-packages/OpenGL/error.py", line 194, in glCheckError
    baseOperation = baseOperation,
OpenGL.error.GLError: GLError(
    err = 1281,
    description = 'invalid value',
    baseOperation = gluBuild2DMipmaps,
    cArguments = (
        GL_TEXTURE_2D,
        4,
        958,
        272,
        GL_RGBA,
        GL_UNSIGNED_BYTE,
        '\x00\x00\x00\x00\x00\x00\x00\x00\x00...,
    ),
    result = 0
)
emma-PC emma # [/I]

[B]I'm new to Linux, I'm a Windows girl. I have no idea what any of this means, when it comes to coding all I understand is html and css. *big sulk*

What do I have to do to make this game work?

Also, while I'm asking this, is there a command similar to Apple's "Force Quit" or Windows Ctrl/Alt/Del?
[/B]

---

### Post by Ericj1186 on 2009-08-05
Did you try Frets of Fire X?  It's a bit more stable from what I understand, and I think it plays the same song files.

---

### Post by guitar_man on 2009-08-05
Did you get the FOF on the repo or you  have the io version?
Its much better to get from the repo....

go to application>>>add/remove>>>games>>>>


look for frets on fire

---

### Post by rednano12 on 2009-08-06
> **guitar_man said:**
> Did you get the FOF on the repo or you  have the io version?
Its much better to get from the repo....

go to application>>>add/remove>>>games>>>>


look for frets on fire

NO.

I highly recommend against this.

The current state of Frets on Fire is this. There is the official version, which receives almost no updates and is most likely going to be abandoned soon, if it hasn't already. Seriously though, they NEVER update it.

The other version is a popular mod known as FoFiX (**F**rets **o**n **Fi**re **X**). It is being developed today, with many amazing features the original never had. Unfortunately, it doesn't run as well on older hardware. You can find FoFiX here: [http://tinyurl.com/l4332c](http://tinyurl.com/l4332c). 

It really depends on your hardware which you choose. If you have an error with FoFiX, you are likely to get the best help here: [www.fretsonfire.net](www.fretsonfire.net)

---

