---
title: "Compiling Ultima Iris"
date: 2007-06-22
forum: Gaming &amp; Leisure
---

### Post by botulismo on 2007-06-22
Has anyone had any luck compiling Ultima Iris under Ubuntu? I found a list of dependencies [here]("http://www.iris2.de/index.php/Building_From_Source") but I'm not able to figure out what their Ubuntu equivalents all are... Anyone know? Thanks!

---

### Post by jpkotta on 2007-06-22
Generally, they will have the prefix "lib" and you will want the suffix "-dev".  Just search in your apt frontend of choice (e.g. synaptic) and get the package with "-dev".  The trickier ones are autotools, because you need to be careful with the versions (note how they specifiy them on the wiki page), and SDL because there are several components and flavors of it.  You probably want the ALSA SDL.

Then you play the game of ./configure (after the bootstrap step) and seeing what's missing (which shouldn't be anything if you got all the deps).

---

### Post by Ripfox on 2007-08-13
Anyone got this working?

---

