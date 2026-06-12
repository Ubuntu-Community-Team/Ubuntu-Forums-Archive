---
title: "chbg Install Trouble"
date: 2007-02-19
forum: Desktop Environments
---

### Post by jackn on 2007-02-19
I'm trying to get my screensaver to project a slideshow. 

According to the [xscreensaver FAQ]("http://www.jwz.org/xscreensaver/faq.html#slideshow"), this should be possible if you use chbg as an xscreensaver client.

I'm running Ubuntu (32-bit Edgy Eft), and some in the forums recommend the xscreensaver-chbg combo for that purpose.

I've downloaded both apps. I've set up xscreensaver, and it's working fine.

I've studied the doc provided for chbg, the man page and other files, but in particular the /usr/share/doc/chbg/xscreensaver- howto.txt file.

It tells me to first set up chbg and get it to work to my satisfaction.

When trying to set it up, however, I get the following error messages:

Code:
```

~$: chbg -setup

Gtk-WARNING **: Failed to load module "libgail.so": libgail.so: cannot open shared object file: No such file or directory

Gtk-WARNING **: Failed to load module " libatk-bridge.so": libatk-bridge.so: cannot open shared object file: No such file or directory
```


Don't know what these messages mean.
The files libgail.so and libatk-bridge.so do exist on my system.
On the net, I cannot find 'shared object file' related to chbg.

I've seen some references to chbg being buggy.
Should I drop it? 
The alternative is XV, a piece of shareware, which goes for $25. Any good?

Help? Thank you kindly.

Jackn

---

