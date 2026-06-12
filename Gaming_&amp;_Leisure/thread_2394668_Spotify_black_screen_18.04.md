---
title: "Spotify black screen 18.04"
date: 2018-06-19
forum: Gaming &amp; Leisure
---

### Post by BinaryJava on 2018-06-19
Installed through snap store through termnal and get this error,

Gtk-Message: Failed to load module "gail"
Gtk-Message: Failed to load module "atk-bridge"
Gtk-Message: Failed to load module "canberra-gtk-module"
ATTENTION: default value of option force_s3tc_enable overridden by environment.
libGL error: No matching fbConfigs or visuals found
libGL error: failed to load driver: swrast
[0619/185034.744582:ERROR:gl_context_glx.cc(227)] Couldn't make context current with X drawable.
[0619/185034.744604:ERROR:gpu_info_collector.cc(62)] gl::GLContext::MakeCurrent() failed
[0619/185047.953744:ERROR:browser_gpu_channel_host_factory.cc(120)] Failed to launch GPU process.

I am running nvidia driver 396.24.02 and it was working a few days ago.

---

### Post by BinaryJava on 2018-06-19
Fixed by installing nvidia driver 390, not sure why it stopped working recently on 396 though.

---

### Post by cactusownage on 2018-07-15
Try launching it with 
[HTML]spotify --disable-gpu[/HTML]
Got the same error on nvidia 396.24.02 too. Spotify worked fine on nvidia 390 for me. But with that command it works.

---

### Post by turb03 on 2018-07-30
> **cactusownage said:**
> Try launching it with 
[HTML]spotify --disable-gpu[/HTML]
Got the same error on nvidia 396.24.02 too. Spotify worked fine on nvidia 390 for me. But with that command it works.


That worked for me thanks :D

---

### Post by uncielser456 on 2018-08-10
> **cactusownage said:**
> Try launching it with 
[HTML]spotify --disable-gpu[/HTML]
Got the same error on nvidia 396.24.02 too. Spotify worked fine on nvidia 390 for me. But with that command it works.

Worked for me too. Thanks!

---

