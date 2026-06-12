---
title: "compiz-fusion"
date: 2008-02-10
forum: Desktop Effects &amp; Customization
---

### Post by Quicksilver21 on 2008-02-10
when i go to system >> preferences >> advanced desktop settings all of the options are greyed out and i cant check or uncheck anything.


any ideas?

---

### Post by Rhubarb on 2008-02-10
Make sure Compiz is turned on.
System --> Preferences --> Appearance
Go to the Visual Effects tab, 
The click on the Custom radio button there to enable compiz.

---

### Post by Quicksilver21 on 2008-02-10
already on custom

---

### Post by Rhubarb on 2008-02-11
Do you know if Compiz Fusion is running at all?
What video card do you have?
Do you have 3D acceleration working with your video card?

---

### Post by chavanak on 2008-02-11
glxinfo | grep ender

type this in a terminal and give the output

---

### Post by Quicksilver21 on 2008-02-11
this is the output of glxinfo | grep ender


direct rendering: Yes
OpenGL renderer string: GeForce 7600 GT/PCI/SSE2
    GL_NVX_conditional_render, GL_SGIS_generate_mipmap, GL_SGIS_texture_lod, 


Do you know if Compiz Fusion is running at all? the effects i enabled before still work
What video card do you have? nvidia 7600gt
Do you have 3D acceleration working with your video card? no clue

---

### Post by tangibleorange on 2008-02-11
Try:

> compiz --replace

and then go back into the editor.

---

### Post by Quicksilver21 on 2008-02-11
nothing changed when i did that

---

