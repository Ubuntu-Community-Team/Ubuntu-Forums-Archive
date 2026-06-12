---
title: "Gnome Terminal slow/hangs when scrolling or cutting and pasting"
date: 2007-02-14
forum: Desktop Environments
---

### Post by wshields on 2007-02-14
I'm running Edgy on a dual core machine (E6300, 2GB DDR2-667, 965 chipset, shared video).  The only installation issue I had was I had to add this boot option:

pci=nommconf

otherwise it hung during boot up.

Anyway, it all works fine except Gnome Terminal has a chronic problem.  If I try and select text to copy or scroll using the mouse wheel it'll hang for 10-20 seconds before it does the request.  It's not consistent either.  Sometimes it works OK but most of the time it doesn't.  It's really irritating.

On a google search I found there was an issue with libvte for some people but that seemed to be a largely Solaris problem (rather than x86) so I'm not sure if it applies to me.  Does anyone else have this problem?  Is there a fix?  Do you need more info?  I'm happy to provide whatever is required.

Cheers

---

### Post by Glenn Jones on 2007-02-14
Hi,

I've also found the Gnome terminal to be frustratingly slow especially in untaring something. I did read somewhere that this is an inherent problem of the terminal. Is this true? Can the Gnome terminal be speeded up?


P.S. I had no issues in installing edgy

---

### Post by gp2x on 2007-02-16
I have this issue too.

I believe there is a fix upstream somewhere. In the meantime Im just using rxvt instead.

---

