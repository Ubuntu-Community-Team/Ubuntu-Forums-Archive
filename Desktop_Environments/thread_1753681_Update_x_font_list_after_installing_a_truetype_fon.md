---
title: "Update x font list after installing a truetype font"
date: 2011-05-09
forum: Desktop Environments
---

### Post by jlv4 on 2011-05-09
Hi there,

I've installed the inconsolata font (ttf-inconsolata) and I'd like to use it as my font in xterm.

```
xlsfonts | grep incon
```This does not show anything up, which presumably means I have to update some font database. Given that ubuntu doesn't ship with xfs anymore (and since it doesn't generally seem to be required, installing it seems fairly pointless), I can't just restart that service. How do I make X aware I've installed a new font and make it available through xlsfonts so I can put it in my .Xresources?

Please note that I'm not using any of the desktop environments so anything specific to any of those won't work for me.

Thanks

---

