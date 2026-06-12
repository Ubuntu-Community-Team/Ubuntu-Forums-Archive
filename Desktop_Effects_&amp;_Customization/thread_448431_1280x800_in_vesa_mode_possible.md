---
title: "1280x800 in vesa mode possible?"
date: 2007-05-19
forum: Desktop Effects &amp; Customization
---

### Post by sartic on 2007-05-19
Any hints how 2 do this?

---

### Post by bimargulies on 2008-03-13
On a dell xps m1330, this is vga=865. However, my virtual terminals are blank when I do this. Blinking cursor, nothing else.

See [http://www.courville.org/mediawiki/index.php/Vesa_modes](http://www.courville.org/mediawiki/index.php/Vesa_modes).

See [http://intr.overt.org/blog/?page_id=56](http://intr.overt.org/blog/?page_id=56).

---

### Post by Zorael on 2008-03-16
Are you sure you're talking about the same thing? If you mean vesa mode as in 'X running the vesa driver', I'm not sure it's possible.

As for terminal resolution, the framebuffer module isn't included in the kernel, so you have to set it up to load manually upon boot. Else you get the black screen.

From memory, the way I did it:
[list]
[*]Add two lines to the end of /etc/modules, one saying 'fbcon' and one saying 'vesafb'
[*]Comment (put a hashmark # in front of) 'vesafb' in the file /etc/modprobe.d/blacklist-framebuffer
[/list]

I'll modify this when I next boot into my Kubuntu installation (later tonight/tomorrow), if I erred somewhere.

---

