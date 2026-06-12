---
title: "problem with XMMS (warty repositorie)"
date: 2005-02-18
forum: Desktop Environments
---

### Post by kosmic on 2005-02-18
I've used synaptic to install XMMS (warty)

and when i type xmms with give's me te follow error :

> Gtk-WARNING **: libgdk_pixbuf.so.2: cannot open shared object file: Arquivo ou d iretório não encontrado

Gtk-WARNING **: libgdk_pixbuf.so.2: cannot open shared object file: Arquivo ou d iretório não encontrado
Inconsistency detected by ld.so: ../sysdeps/generic/dl-tls.c: 72: _dl_next_tls_m odid: Assertion `result <= _rtld_local._dl_tls_max_dtv_idx' failed! 


Anybody knows howto put xmms working again ?

---

### Post by foobar on 2005-02-20
bump

i now have this problem too
```
libmikmod.so.2: cannot open shared object file: No such file or directory
Inconsistency detected by ld.so: ../sysdeps/generic/dl-tls.c: 72: _dl_next_tls_modid:
 Assertion `result <= _rtld_local._dl_tls_max_dtv_idx' failed!

```

---

### Post by foobar on 2005-02-20
*from another thread*
```

$ sudo apt-get install Libmikmod2

```
it fixed the prob

---

### Post by kassetra on 2005-02-20
I have a suggestion also, if xmms gives you any more problems...  you might want to try beep-media-player...  
 
 beep-media-player is essentially xmms for gtk2, which means that it works better with the default setup that ubuntu provides in warty.  Also, all of the skins & plugins from xmms work in beep-media-player... soooo....
 
 If you have any more troubles (fonts are ugly, having to use the gtk1 file chooser, etc.) ... you might want to give beep-media-player a try.

---

