---
title: "WoW runs in D3D, but crashes in opengl"
date: 2006-11-01
forum: Gaming &amp; Leisure
---

### Post by glave on 2006-11-01
I just got WoW working last night, but oddly enough, I can only get it to work in D3D. If I try to launch using opengl, it crashes nearly immediately, I don't even get the login screen. D3D works, but performance could definintely be a lot better.

A little info, I'm using 0.9.24 wine recompiled with the nvidia patch. Edgy Eft, and I've got the nvidia driver installed and working. I have dual Geforece 6800 GT's, but I'm currently only using 1, I haven't even tried to get the other going since coming over to linuz. 

Any idea where to begin?

---

### Post by Steeljaw on 2006-11-01
I had the same problem.

The solution for me was to downgrade to 0.9.22 wine. :(

I compiled it from source and it works like a charm. Now have a bit of a frame rate issue (getting 15-30 fps instead of the usual 50-60). But I'm sure that's a mistake from my side.

---

### Post by Ferrat on 2006-11-01
> **Steeljaw said:**
> I had the same problem.

The solution for me was to downgrade to 0.9.22 wine. :(

I compiled it from source and it works like a charm. Now have a bit of a frame rate issue (getting 15-30 fps instead of the usual 50-60). But I'm sure that's a mistake from my side.

Wine 0.9.23 works aswell but yes the openGL is broken in 0.9.24

---

### Post by glave on 2006-11-01
I actually just stumbled across a post at wine that details this as a bug. 0.9.24 has the bug, but I just downgraded to 0.9.23 and its working perfectly...!

---

### Post by StomUK on 2006-11-01
Hmm.. I will have to give .23 a go then - where can I get the sources for .23 from now? I did briefly look about the other day but only came up with .24 (which no matter what I try when compiling crashes out with opengl :) )

---

### Post by Ferrat on 2006-11-01
> **StomUK said:**
> Hmm.. I will have to give .23 a go then - where can I get the sources for .23 from now? I did briefly look about the other day but only came up with .24 (which no matter what I try when compiling crashes out with opengl :) )

check the appdb for wine/wow, they have a list i think with older versions

---

### Post by simplyw00x on 2006-11-01
I got this with 0.9.23, and the solution was to run in full-screen, not windowed.

---

