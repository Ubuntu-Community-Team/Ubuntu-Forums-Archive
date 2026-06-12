---
title: "WoW is too slow!"
date: 2005-10-04
forum: Gaming &amp; Leisure
---

### Post by St3althcAt on 2005-10-04
I've managed to successfully install and run WoW, so forget my other posts. The problem now is that I play WoW on Linux with lower settings than in Windows, and I get an average 15-20 fps and on Windows, with even more details on, I get 30-35 fps. I think this is not normal right? Can someone help me? Thank you!

---

### Post by jeffreyvergara.NET on 2005-10-04
you must installed the latest Video card driver

---

### Post by St3althcAt on 2005-10-04
Latest drivers installed, downloaded yesterday from the ATi website.

---

### Post by jyank on 2005-10-04
have you tried it in both opengl mode and d3d?

---

### Post by St3althcAt on 2005-10-04
Direct3D doesn't work for me. OpenGL is the one that has this "slowness".

---

### Post by jeffreyvergara.NET on 2005-10-04
I guess it's because it's OpenGL?

and btw, what program did you use? Wine? Cedega?? I have some issue with wine, some of my games run slow using Wine, but not in cedega

---

### Post by Dolphin on 2005-10-04
OpenGL runs faster than D3D in most cases.

Stealth, the reason it's running slower is because you're using ATI.  ATI is phenominal in a windows environment IMO.  In linux, not so much.  They are finally making a larger effort to have competetive drivers, and their efforts have at least made ATI do-able in linux now.  But they're not caught up yet.  If you want the same or better performance in linux, then you need nvidia.  Otherwise my advice would be just to be patient.  ATI's drivers are slowly getting better.

---

### Post by seethru on 2005-10-04
Also try turning Pixel Shaders down to 1.1.
Check Fixed GL Extension Buffer
Under Manual GL Extensions put -GL_ARB_vertex_buffer_object
Set Fixed Program to Auto
Fragment Offset to Tex
Non Power of Two Textures to Yes

---

### Post by jyank on 2005-10-04
[QUOTE=Dolphin]OpenGL runs faster than D3D in most cases.
Stealth, the reason it's running slower is because you're using ATI.  ATI is phenominal in a windows environment IMO.  In linux, not so much.  They are finally making a larger effort to have competetive drivers, and their efforts have at least made ATI do-able in linux now.  But they're not caught up yet.  If you want the same or better performance in linux, then you need nvidia.  Otherwise my advice would be just to be patient.  ATI's drivers are slowly getting better.[/QUOTE]

It's not always the case, I'm using an ATI card (9800 PRO) and I get the same frame rate I get in windows, sometimes, though, it goes down a little lower but other than that it's 100% playable.

I always use cedega for my games, never tried point2play because cedega always worked fine.  What error are you getting with D3D? In my situation with wow, D3D runs a lot better with a higher FPS than opengl.  Plus, with opengl the sound lags a few seconds.  IE: running from ironforge to dun murogh, i can still hear the ironforge music when im halfway down the hill

---

### Post by Perfect Storm on 2005-10-04
It' diffently better to run Wow with commercial Cedega. It runs smoothly on my system with full details on 1600x1200 res.

---

