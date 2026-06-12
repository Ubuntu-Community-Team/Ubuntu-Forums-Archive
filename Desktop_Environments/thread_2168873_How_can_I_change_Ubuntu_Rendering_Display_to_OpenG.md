---
title: "How can I change Ubuntu Rendering Display to OpenGL?"
date: 2013-08-19
forum: Desktop Environments
---

### Post by ubentobox on 2013-08-19
Hey Everyone, 

I am working on a project with the Oculus Rift, and I wanted to know if anyone here knows if I can change it so Ubuntu uses OpenGL for a display engine as opposed to what it uses now.  In order to run the Rift you need to have specific functions, while available on linux require OpenGL to be active.  My project would include running ubuntu from launch through the Rift, so OpenGL from power state on.

Any suggestions or topics I should defer too?  I know this is a can of worms but I want to know what I am going to ask someone else to do before I dump a huge pile of trouble in someone's lap.

Thanks

---

### Post by lukeiamyourfather on 2013-08-19
If the graphics hardware and graphics drivers support OpenGL then there should be no problem. What hardware are you using, what driver are you using? What version of Ubuntu?

---

### Post by r_avital on 2013-08-19
Ubentobox, 

Did you install the packages mesa-utils and mesa-utils-extras?  If not, give it a try, they should bring with them an entire set of GL libraries (apologies in advance if I'm completely off-base on this).  Install them from Synaptic.

Good luck

---

