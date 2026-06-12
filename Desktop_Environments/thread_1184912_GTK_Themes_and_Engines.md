---
title: "GTK Themes and Engines"
date: 2009-06-11
forum: Desktop Environments
---

### Post by Sigurd Suhm on 2009-06-11
So after accidentally suddenly messing up my themes I was toying around for days trying to get stuff back to normal. After tons of installing, compiling, reinstalling, reconfiguring and so on of various engines and packages I seem to have figured out the core of the problem.

Basically my Metacity seems to look for both themes within the /usr/local/share folder while the actual installs are usually put in /usr/share (engines: /usr/lib/gtk-2.0 should be /usr/local/lib/gtk-2.0).

Can anyone shed some light on this? I've kinda solved it by simply moving the relevant files to the correct folders. But it does seem kinda strange to me.

Thanks in advance
Sigurd

---

