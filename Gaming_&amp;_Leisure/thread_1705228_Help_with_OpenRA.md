---
title: "Help with OpenRA?"
date: 2011-03-11
forum: Gaming &amp; Leisure
---

### Post by xondak on 2011-03-11
Can anyone help me out with this? I'm running 10.10, with an Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c). I'm trying to play OpenRA. The screen goes black for a second and then I'm returned to my terminal. When I launch it from the terminal, this is the entire output:

```
/usr/share/themes/Human/gtk-2.0/gtkrc:85: Murrine configuration option "gradients" is no longer supported and will be ignored.
/usr/share/themes/Human/gtk-2.0/gtkrc:100: Murrine configuration option "scrollbar_color" is no longer supported and will be ignored.
Using Gl renderer

Unhandled Exception: System.InvalidOperationException: GL Error: 1282
  at OpenRA.Renderer.Glsl.GraphicsDevice.CheckGlError () [0x00000] in <filename unknown>:0 
  at OpenRA.Renderer.Glsl.Shader..ctor (OpenRA.Renderer.Glsl.GraphicsDevice dev, System.String type) [0x00000] in <filename unknown>:0 
  at OpenRA.Renderer.Glsl.GraphicsDevice.CreateShader (System.String name) [0x00000] in <filename unknown>:0 
  at OpenRA.Graphics.Renderer..ctor () [0x00000] in <filename unknown>:0 
  at OpenRA.Game.Initialize (OpenRA.Arguments args) [0x00000] in <filename unknown>:0 
  at OpenRA.Program.Run (System.String[] args) [0x00000] in <filename unknown>:0 
  at OpenRA.Program.Main (System.String[] args) [0x00000] in <filename unknown>:0 

```

I'd really like to play this game, anybody know what the problem might be?

---

### Post by flaak_monkey on 2011-03-15
Do you have the GMA 950, or X3100 gfx card? Because that chipset is for a few differnt intergrated INTEL GMA cards.

---

### Post by ELD on 2011-03-15
Make sure you submit a bug report on their tracker, mine is a similair issue and i have reported it to no reply though.

---

### Post by sinbowden on 2011-08-09
I have the same problem! 


Unhandled Exception: System.InvalidOperationException: GL Error: 1282
  at OpenRA.Renderer.Glsl.GraphicsDevice.CheckGlError () [0x00000] in <filename unknown>:0 
  at OpenRA.Renderer.Glsl.Shader..ctor (OpenRA.Renderer.Glsl.GraphicsDevice dev, System.String type) [0x00000] in <filename unknown>:0 
  at OpenRA.Renderer.Glsl.GraphicsDevice.CreateShader (System.String name) [0x00000] in <filename unknown>:0 
  at OpenRA.Graphics.Renderer..ctor () [0x00000] in <filename unknown>:0 
  at OpenRA.Game.Initialize (OpenRA.Arguments args) [0x00000] in <filename unknown>:0 
  at OpenRA.Program.Run (System.String[] args) [0x00000] in <filename unknown>:0 
  at OpenRA.Program.Main (System.String[] args) [0x00000] in <filename unknown>:0

---

### Post by xondak on 2011-11-19
If you guys are still having trouble getting this to work and you have the Intel chipset, try 

```
sudo apt-get install nvidia-cg-toolkit
``` 

It worked for me. Enjoy!

---

