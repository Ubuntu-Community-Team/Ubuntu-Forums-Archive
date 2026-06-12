---
title: "PSPP / PSPPIRE Install"
date: 2008-10-04
forum: Education &amp; Science
---

### Post by RJWEcology on 2008-10-04
Hey, 

Having left openSUSE for Ubuntu (am very pleased I've done so) I have instaled PSPP 0.4.0 on my 8.04 Hardy Heron. I wanted to know how I can add the PSPPIRE GUI to PSPP. Do I need to add the packages required to 0.4.0 or do I need to download the 0.6.0 code, add the packages and ./configure again? 

```
The following packages are required to enable PSPPIRE, the graphical
user interface for PSPP.  If you cannot install them or do not wish to
use the GUI, you must run `configure' with --without-gui.

    * pkg-config (http://pkg-config.freedesktop.org/wiki/).  Versions
      0.18 and 0.19 have a bug that will prevent library detection,
      but other versions should be fine.

    * GTK+ (http://www.gtk.org/), version 2.12.0 or later.

    * libglade (http://www.jamesh.id.au/software/libglade/), version
      2.6 or later.
``` 

What is the best way to check I have these? Sorry if I'm slow, I've come from using YaST so I'm a bit lost here. Any help and advice would be greatly appreciated. 

Thanks, 

Rich

---

### Post by UbuWu on 2008-10-04
Using PSPP 0.6.0 is probably the best option, it has the gui included. Ubuntu 8.10 (intrepid) has it in the repositories, so you could consider upgrading to that (still beta) and then you don't have to compile anything (or wait a few weeks until it is final).

---

### Post by RJWEcology on 2008-10-04
I downloaded the 0.6.0 version and compiled it myself. I had to add a few things from the Synaptic package manager but it all works like a charm! I'm very pleased!!! 

I'm extremely new to linux (about 2 months now) but now I have PSPP and a few other things, I'm not looking back. It's a steep learning curve but I'm getting there. I came from openSUSE but it had too many problems. I'm liking Ubuntu very much!

---

### Post by tommie74 on 2008-12-13
Here is a 0.6 deb installation for ubuntu 8.04

[http://www.getdeb.net/release/3411](http://www.getdeb.net/release/3411)

---

