---
title: "Strange Flash problem, many crashes and re-sesion"
date: 2009-05-27
forum: General Help
---

### Post by slamelov on 2009-05-27
Hi

I'm using Ubuntu 9.04 in this system:
- Intel 3.4 ghz
- nVidia 7900 Ultra
- 2Gb Ram Kingston
- Sound blaster Live
- Asus P4V800D-X motherboard

When I use the Internet Browser (Opera or Firefox) in a web site with some kind of Flash, the system goes unstable and browser crash to desktop. Some times, sesion finishes also. Really I'm not sure if it's Flash or some other script, but always happens with flash.

Any help?

---

### Post by hal8000 on 2009-05-27
Start firefox from the terminal, this may redeem some useful output when it crashes

---

### Post by slamelov on 2009-05-27
SWFDEC: ERROR: swfdec_video_decoder_gst.c(156): swfdec_video_decoder_gst_decode:failed to pull decoded buffer. Broken stream?


That problem appears continuosly. Is there any log where to check?

---

### Post by Soul-Sing on 2009-05-27
Are you running flash non free? ===> synaptic: with the ubuntu-restricted-extra package?
If so:
```
sudo aptitude purge swfdec
```

But you also could consider using Gnash 0.8.5( common) and the Gnash mozilla plugin. An excellent alternative for using flash non free. Gnash 0.8.5 is in the repos. of ubuntu 9.04.
Its open source and great stuff.

---

### Post by slamelov on 2009-05-27
I'm using non free. I'll check with gnash

Edit: I purged SWFDEC and the same message appears:

SWFDEC: ERROR: swfdec_video_decoder_gst.c(156): swfdec_video_decoder_gst_decode: failed to pull decoded buffer. Broken stream?

---

