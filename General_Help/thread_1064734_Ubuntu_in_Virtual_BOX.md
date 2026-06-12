---
title: "Ubuntu in Virtual BOX"
date: 2009-02-09
forum: General Help
---

### Post by nvoliveira on 2009-02-09
Good Morning,

I have a problem about activating Compiz-fusion.

When I try to activate in System>Preferences>Appearance, say an error "It's impossible activate visual effects."

What I need to do? I read in a tipic the checklist I need to do, but I don't know how to do it?

Sorry I'm very newbie at UBUNTU.

---

### Post by HavocXphere on 2009-02-09
Probably won't work. The virtualization puts an extra layer inbetween the OS and the Hardware, so the software can't talk directly to the graphics card.

---

### Post by HyRax on 2009-02-09
Won't work - the version of Virtualbox currently on public release (2.1.2) does not yet support OpenGL for Linux guests - [it only works for Windows guests](http://www.youtube.com/watch?v=XiZyigv_aRc).

However, apparently Sun themselves are about 2-3 versions ahead internally, and currently have OpenGL in Linux guests working very well on Solaris hosts atm.

---

### Post by Muhammad Aalijah on 2009-02-09
Would this also be true for any adobe flash issue which may occur in Virtualization? Although the web browser indicates that flash is installed but on visiting flash websites flash components do not function.

---

### Post by RedSingularity on 2009-02-09
It would be nice if they could get the Compiz effects into Virtual Linux.  I am sure they will over time.

---

### Post by HavocXphere on 2009-02-09
> **Muhammad Aalijah said:**
> Would this also be true for any adobe flash issue which may occur in Virtualization? Although the web browser indicates that flash is installed but on visiting flash websites flash components do not function.
Probably not. That is in all likelihood a real issue not caused by virtualization. *UNLESS* flash displays its output via opengl like some video players do. (Not sure whether or not this is the case)

---

### Post by HyRax on 2009-02-09
Flash is working fine for me in Virtualbox, under both Windows and Linux guests - nothing special needed to be done - just install like any normal real installation.

---

### Post by SCGhst1 on 2009-02-09
are you sure it wont work? Try with the newest version you can enable 3d acceleration in virtualbox. and it might also depend on you video card

---

### Post by HyRax on 2009-02-09
OpenGL Support in Virtualbox 2.1.2 only applies to Windows guests at this moment in time. It's the Virtbualbox Additions driver that tells Windows that the "video card" is 3D capable. The Additions driver for Linux does not report that yet, hence Compiz in a Linux guest is not possible just yet.

Read the changelog on the Virtualbox website!

---

