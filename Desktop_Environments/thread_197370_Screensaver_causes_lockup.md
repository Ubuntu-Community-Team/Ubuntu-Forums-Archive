---
title: "Screensaver causes lockup"
date: 2006-06-15
forum: Desktop Environments
---

### Post by nmehsr on 2006-06-15
I've been having problems with ubuntu randomly going into a lockup recently. Now it mainly seems to only happen when the screensaver activates, maybe its something in the 3d drivers idk. I tried to get rid of the screensaver but going into the screensaver menu in preferances just got me another immediate freeze. This is my first week on any linux distro so i'm just sorta confused.

I'm running
2.67 Ghz P4
Radeon 9700 pro
1 gig pc-3200
Dual booting with XP

*edit* if noone can help me with the lockup can you just help me turn off my screensaver through console so i don't have to fear walking away from my computer?

---

### Post by nmehsr on 2006-06-15
I hate to bump but i really would just like some alternative way of shutting off my screensaver at least.

---

### Post by nmehsr on 2006-06-15
i'm gonna give this one more shot

---

### Post by zalberico on 2006-06-15
Hey! yeah I really have no way at all to help you, except to bump your thread up to the top so... 
your welcome
zman14321

---

### Post by Mamboyin on 2006-06-16
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

install real ati drivers. 

if you havve older graphics card ( radeon 8500, one should install the previous driver with same instructions, that is still working. I writed this for other, you seem to have 9700pro )

---

### Post by nmehsr on 2006-06-17
Thanks that did it!:p

---

### Post by herot on 2006-06-18
Mamboyin, how can i undo what "method 1" did in the "real ATI driver" installation faq that you posted... GL was working fine (with neverwinter nights...) but i had the screensaver lockup problem so i thought it would help if i tried the faq method... but it messed gl up... 

here is fglrxinfo output:
```

[fglrx] API ERROR: could not register entrypoint for SelectTextureSGIS
[fglrx] API ERROR: could not register entrypoint for SelectTextureTransformSGIS
[fglrx] API ERROR: could not register entrypoint for ClientActiveVertexStreamATI[fglrx] API ERROR: could not register entrypoint for VertexBlendEnviATI
[fglrx] API ERROR: could not register entrypoint for VertexBlendEnvfATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream2dvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream3dvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4sATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4svATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4iATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4ivATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4fATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4fvATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4dATI
[fglrx] API ERROR: could not register entrypoint for VertexStream4dvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3bATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3bvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3sATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3svATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3iATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3ivATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3fATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3fvATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3dATI
[fglrx] API ERROR: could not register entrypoint for NormalStream3dvATI
[fglrx] API ERROR: could not register entrypoint for DrawRangeElementsEXT
[fglrx] API ERROR: could not register entrypoint for WeightbvARB
[fglrx] API ERROR: could not register entrypoint for WeightsvARB
[fglrx] API ERROR: could not register entrypoint for WeightivARB
[fglrx] API ERROR: could not register entrypoint for WeightfvARB
[fglrx] API ERROR: could not register entrypoint for WeightdvARB
[fglrx] API ERROR: could not register entrypoint for WeightubvARB
[fglrx] API ERROR: could not register entrypoint for WeightusvARB
[fglrx] API ERROR: could not register entrypoint for WeightuivARB
[fglrx] API ERROR: could not register entrypoint for WeightPointerARB
[fglrx] API ERROR: could not register entrypoint for VertexBlendARB
[fglrx] API ERROR: could not register entrypoint for MultiDrawArraysEXT
[fglrx] API ERROR: could not register entrypoint for MultiDrawElementsEXT
[fglrx] API ERROR: could not register entrypoint for DrawBuffersATI
[fglrx] API ERROR: could not register entrypoint for DrawElementsFGL
[fglrx] API ERROR: could not register entrypoint for DrawWireTrianglesFGL
[fglrx] API ERROR: could not register entrypoint for PNTrianglesiATI
[fglrx] API ERROR: could not register entrypoint for PNTrianglesfATI
[fglrx] API ERROR: could not register entrypoint for TexBumpParameterivATI
[fglrx] API ERROR: could not register entrypoint for TexBumpParameterfvATI
[fglrx] API ERROR: could not register entrypoint for GetTexBumpParameterivATI
[fglrx] API ERROR: could not register entrypoint for GetTexBumpParameterfvATI
[fglrx] API ERROR: could not register entrypoint for BeginVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for EndVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for BindVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for GenVertexShadersEXT
[fglrx] API ERROR: could not register entrypoint for DeleteVertexShaderEXT
[fglrx] API ERROR: could not register entrypoint for ShaderOp1EXT

...

etc, etc, etc..

```

i have a Radeon 9000 Pro (R250??) was this driver method for me??? anyway i guess i need to go back to the way it was...
[COLOR="Red"]
*UPDATE* nevermind i figured it out, it had backed up my original xorg.conf so i just renamed it and used my original and everything is back right again... i dont know why gnome-screensaver locks up... i just apt-get removed it.. so now it cant lock my system up![/COLOR]

---

