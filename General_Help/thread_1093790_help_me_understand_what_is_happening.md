---
title: "help me understand what is happening"
date: 2009-03-11
forum: General Help
---

### Post by thehighhat on 2009-03-11
Any thoughts about this...

setup:

[LIST]
[*]x86_64  
[*]hardy  
[*]either server or generic kernel  
[*]8 gb memory
[*]8 cores (2 x 2.33ghz xeon)
[*]nvidia gtx 280; 177.x drivers
[*]2 x 1920x1200 monitors
[/LIST]

test:
[INDENT]run top in a terminal; press "1" to see each cpu separately
start as many glxgears as cores; make sure they do not overlap
*note the cpu usage for each core*[/INDENT]

observations:
[INDENT]without compiz:
[INDENT]    if nvidia is set to vblank; then
[INDENT]      xserver usage goes up ~30% on one cpu
      the other cpus show no load
      all glxgears running normally[/INDENT]
   if nvidia is set not to use vblank; then
      [INDENT]xserver usage goes up not as much
      each cpu shows high load; ~ 80-100%
      all glxgears running smoothly[/INDENT][/INDENT]
 with compiz:
    [INDENT]vblank on/off no difference
    all cpus at full load 100%
    redraw issues with glxgears[/INDENT][/INDENT]

notes:
 [INDENT] antialiasing or anisotropic do not change above results noticeable
  triple buffer has no effect
[/INDENT]

on reproducing:
  you may need to stop compiz and restart to reproduce when changing nvidia settings


questions:

**why?**  

what does compiz do that sends the cpu load so high?  
especially when the non-compiz vblank version runs w/o any issues and w/o any cpu load?

---

