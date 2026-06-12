---
title: "Use vm ware to run battlefield 2142?"
date: 2007-05-24
forum: Gaming &amp; Leisure
---

### Post by nal on 2007-05-24
Im wondering since cedega can support bf 2142 but its slow if I would have a better speed if i just made a vm installation of win xp and install and play the game by that means.  Has anyone tried this and if so did it work well?

---

### Post by earobinson on 2007-05-24
Im told that vmware will always be slower than wine or cedaga this is due to the fact that vmware is an emulator vs cedaga and wine just provide the api

---

### Post by BoneyOne on 2007-05-24
The last I knew (may have changed) is that VMWare used a "virtual" video card instead of directly accessing your actual card like Cadega and Wine do.

Do to this 3d acceleration is pretty much shot so it makes playing games difficult if not completely impossible.

---

### Post by earobinson on 2007-05-25
Im pretty sure the feisty kernel lets programs like qemu and vmware directly use your card however there is still a lot of emulation so things will never be as fast as they can be with wine.

try checking your wine settings ```
winecfg
``` see if there are any extra options that you can enable or disable, make sure you turn off any emulation.

---

### Post by tht00 on 2007-05-25
VMware uses software emulation to create and run the OS.  Emulation will always be slower than native speeds.

Cedega/Wine are extremely close to 'native' speeds (it's a compatibility layer) as they interface the Dx and Windows API directly to OpenGL and X (Gtk?).  

Native (Windows in this case) will always be faster (with a few rare exceptions).  Emulation (for games) is unusable -- at least for now.

---

