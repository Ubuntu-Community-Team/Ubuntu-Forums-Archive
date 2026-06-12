---
title: "Hardware decoding in Steam In-Home-Streaming"
date: 2015-07-31
forum: Gaming &amp; Leisure
---

### Post by eNRGy on 2015-07-31
Hi,

I have an Ubuntu 15.04 laptop which I use quite effectively to stream Windows games from my big Windows gaming machine. Primusrun lets me run games natively on the laptop using the NVidia GPU on demand, and certainly works perfectly well. However I cannot get Steam to use hardware decoding when streaming at all! Whether I start Steam with or without primusrun I get the following error:
"Failed to open VDPAU backend libvdpau_i965.so: cannot open shared object file: No such file or directory"

Steam then falls back on software decoding, which is disappointingly slow and ugly.

libvdpau_i965.so I believe refers to my laptop's Intel GPU which should have VDPAU support, I would have thought. I'm not sure why it would be looking for that missing library when it's running through primusrun.

What can I do to get hardware decoding from either of the GPU's in this laptop? I don't expect it matters which.

Thanks.

---

