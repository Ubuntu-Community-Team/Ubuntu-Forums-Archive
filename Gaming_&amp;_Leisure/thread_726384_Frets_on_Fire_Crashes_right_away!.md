---
title: "Frets on Fire Crashes right away!"
date: 2008-03-16
forum: Gaming &amp; Leisure
---

### Post by jfactor on 2008-03-16
Hello, I have recently installed Frets on Fire through the Synaptic Package Manager,

I click on the game, it loads up to a black screen with a cursor then crashes. 

I am using Gutsy 64-bit with an NVidia 6150 video card, 

her is my glxinfo | grep render output:
direct rendering: Yes
OpenGL renderer string: GeForce Go 6150/PCI/SSE2
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod,

and the error output when I try to open the game:
Traceback (most recent call last):
  File "./FretsOnFire.py", line 64, in <module>
    engine = GameEngine(config)
  File "/usr/share/games/fretsonfire/game/GameEngine.py", line 166, in __init__
    self.svg = SvgContext(geometry)
  File "/usr/share/games/fretsonfire/game/Svg.py", line 78, in __init__
    self.setGeometry(geometry)
  File "/usr/share/games/fretsonfire/game/Svg.py", line 91, in setGeometry
    geometry[2], geometry[3])
  File "/usr/share/games/fretsonfire/game/DummyAmanith.py", line 42, in SetViewport
    glViewport(x, y, w, h)
ctypes.ArgumentError: argument 3: <type 'exceptions.TypeError'>: wrong type

Can anyone help me resolve this issue.
The game works somewhat when I download it from the site and just play it from the tar.gz package. However I don't like playing it this way cuz it doesnt play properly. 

Thanks
JFactor

---

### Post by Gigopepo on 2008-05-02
Same problem here.

Using Gutsy 64 bit too.
Bur with nvidia 7900 gt.

---

### Post by jnuz on 2008-05-02
[http://ubuntuforums.org/showthread.php?t=777060](http://ubuntuforums.org/showthread.php?t=777060)

try that out, not sure if it'll work on x64 though as i compiled it under a 32-bit environment.

---

### Post by Ag_Smith on 2008-05-10
download the last version of frets on fire from its official site this solve this issue but not solve the problem with song.ogg guitar.ogg and ritm.ogg you must merge they into only one song.ogg to work 50%

---

