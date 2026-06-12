---
title: "Dota 2 needs OpenGL extension update"
date: 2015-09-26
forum: Gaming &amp; Leisure
---

### Post by campanella-alex on 2015-09-26
Just a week ago I was playing Dota 2 no problems (on Steam).
After updating (many times) in the past couple days, I keep getting this error:

CheckGLExtensions():
Required OpenGL extension "GL_ARB_separate_shader_objects" is not supported.  Please update your OpenGL driver.

I'm not sure if this is saying I need this extension, or I already have it and it's not supported.  I'm also not sure how to update the OpenGL driver.  When I search on the Synaptic Package manager there's a billion mesa/open gl things listed, but I haven't installed that many of them...

I'm still Linux nooooooobie and happy to have to receive any and all responses thank you =)

Linux campy-TP550LA 3.19.0-28-generic #30~14.04.1-Ubuntu SMP Tue Sep 1 09:32:55 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by cimarron.argento on 2016-03-05
needs updated video drivers:

sudo add-apt-repository ppa: oibaf/graphics-drivers
and update your Ubuntu with the package herein.

[https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)

---

