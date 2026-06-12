---
title: "run specific apps in a 16bit color"
date: 2005-12-22
forum: General Help
---

### Post by chronusdark on 2005-12-22
is there a way to run a particular app (fullscreen) in 16bit depth without reconfigureing xorg.conf and restarting X?

i need to run visualboyadvance in 16 bit depth because its really slow in 24

---

### Post by localzuk on 2005-12-22
You could install xnest and run a second login of X in it.

From a command line something like Xnest -depth 16 -geometry 800x600 would give you a nested x session in a window of your current one with size 800x600 at 16bit. I think you can also do this to a specific application but am unsure how.

---

