---
title: "problem in GLX?"
date: 2007-06-27
forum: Desktop Effects &amp; Customization
---

### Post by mpneerkaje on 2007-06-27
I was playing with settings for compiz and beryl for some time, it gave me the following error:

[COLOR="Red"]compiz --replace&[/COLOR]
/usr/bin/compiz.real: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
inotify_add_watch: No such file or directory

[COLOR="Red"]emerald --replace&[/COLOR]
No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32
/usr/bin/compiz.real: No GLXFBConfig for depth 32


Why all these errors? I have a problem that when i enable desktop effects, the title bar of the windows disappear. I suspect the problem is because of this GLX error. Any idea how to solve these problems?

---

