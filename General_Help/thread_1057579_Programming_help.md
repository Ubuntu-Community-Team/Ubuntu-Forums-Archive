---
title: "Programming help"
date: 2009-02-01
forum: General Help
---

### Post by Eggbertx on 2009-02-01
I'm kind of a noob to programming, and a total noob to non-IDE programming. I want to make custom plugins for [Rockbox]("http://www.rockbox.org"), and (eventually) games. I know I need the source, but where do I go from there? What files do I edit? What file(s) do I compile, or just the one i modified? How do I make it into rockbox format? (.rock) Thank you for your help.

P.S. Oh, I'm not sure if this is important, but I'm using Sansa e260. I already have gcc installed.

---

### Post by jpkotta on 2009-02-02
You probably need gcc, but you will also need a cross-compiler, which is relatively easy to setup with rockbox, IIRC.  The only way to figure it out is to start reading the code.  Pick a simple plugin, like a stopwatch or something, try to find the main source files for it, and figure out how they work.  It will seem impossible at first, but after a while you'll start to grasp it.  Also, look around on the Rockbox wiki and forums.

---

### Post by jpkotta on 2009-02-02
Here we go, good documentation: docs/README, docs/PLUGIN_API

---

