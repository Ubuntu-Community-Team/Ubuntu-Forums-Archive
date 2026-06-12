---
title: "getting ps2pdf to invoke gs-afpl (Aladdin GS)"
date: 2006-01-16
forum: General Help
---

### Post by Sham on 2006-01-16
I have a small problem using ps2pdf when converting slide shows made in LateX. The ps to pdf conversion causes the orientation of the slides to be portrait rather than landscape. Apparently using Aladdin ghostscript will remedy this.

ps2pdf is supposed to invoke ghostscript, which when done now invokes gs-esp:

gs>
ESP Ghostscript 7.07 (2003-07-12)

when I need it to invoke gs-afpl. I wrote an alias in .bashrc to use gs-afpl as gs (which works), but no improvement was seen when running ps2pdf. Is there anyway of seeing which interpreter is being used when ps2pdf is run? 

If I try to remove gs-esp in Synaptic, it says its going to remove ubuntu-desktop!

Any help would be great.

---

### Post by Sham on 2006-01-17
Anyone have any ideas at all? :( 

Sham

---

