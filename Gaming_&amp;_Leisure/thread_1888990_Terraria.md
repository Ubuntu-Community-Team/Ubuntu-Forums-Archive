---
title: "Terraria"
date: 2011-11-30
forum: Gaming &amp; Leisure
---

### Post by Arukas on 2011-11-30
I've read that Terraria is written in C#.  I know linux has some support for c#.  

So does that mean terraria can run in Ubuntu easily?  I read some stuff on how to install terraria on ubuntu and it seem overly complicated.  

-Thanks

---

### Post by pieman711 on 2011-11-30
Unfortunately it's not as easy as which language it's written in. Most games are written in a language supported in linux, in fact most languages are supported by linux. The problem is how the program is written. Most likely it will be written to run with direct x and using other bits that can't run in linux. 
If the source was available it may be possible to try and alter the parts that depend on windows to run to make it work with linux. A quick look on their site and it doesn't look likely, even if it was it would still be quite a task assuming you were already good at C#.

Your best hope is to try using Wine ([http://appdb.winehq.org/objectManager.php?sClass=application&iId=13082](http://appdb.winehq.org/objectManager.php?sClass=application&iId=13082)) or finding a similar game that does run well in linux.

---

### Post by Christian Knudsen on 2011-12-01
I believe it's also using XNA, which will make a Linux version even harder to achieve.

---

### Post by Sofox on 2011-12-01
Actually, there is a Linux port of XNA called MonoGame that recently had their 1.0 release. I'm not sure exactly what is involved to run Terraria on MonoGame, but I think the developers will need to want to make a port. Maybe you should (politely and respectfully) ask them?

---

### Post by Christian Knudsen on 2011-12-01
> **Sofox said:**
> Actually, there is a Linux port of XNA called MonoGame that recently had their 1.0 release.

Cool! I knew there was work being done on Linux ports of XNA, but I didn't realize some of those projects were at such a mature state. :)

---

