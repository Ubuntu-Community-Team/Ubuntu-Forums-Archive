---
title: "Rip CD via Nautilus mount"
date: 2009-11-06
forum: Desktop Environments
---

### Post by kumoshk on 2009-11-06
How does nautilus rip CDs when you copy and paste the wav files through the Nautilus GUI?

I mean, does it use cdparanoia, or some other way? What settings does it use with whatever program it uses?

I'm curious because it's notably faster than typing cdparanoia -B and nothing else, and I want to find out how to use its method from a script.

I'm using Karmic Koala, but I think it was this way in Jaunty, too.

---

### Post by kumoshk on 2010-04-13
Well, I'm not sure exactly how it does it, but I can do it through the command-line with the regular cp command (as long as it's pre-mounted): e.g.

cp ~/.gvfs/"cdda mount on sr0"/* ./

---

