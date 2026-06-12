---
title: "black screen on live cd - I know cd works and I hear sound"
date: 2009-04-12
forum: General Help
---

### Post by pkarza on 2009-04-12
Hello all...

I have a TOSHIBA flatscreen 27" LCD monitor that I know works with XP, and I have a working live 8.1 CD/DVD that I have confirmed to work on another comptuer.

When booting with the TOSHIBA monitor (and I believe this is where the problem is) I get the boot screen, and then I get the nice graphical loading screen... then the screen flickers (out of sync?).  I then hear the nice startup music and I'm stuck.

I was able to use the vga=771 option and by using ctrl-alt-F1 got a text screen... partial success...

How can I change the screen resolution and restart xserver?

Thanks...
... stumped at midnight...

---

### Post by DeMus on 2009-04-12
> **pkarza said:**
> Hello all...

I have a TOSHIBA flatscreen 27" LCD monitor that I know works with XP, and I have a working live 8.1 CD/DVD that I have confirmed to work on another comptuer.

When booting with the TOSHIBA monitor (and I believe this is where the problem is) I get the boot screen, and then I get the nice graphical loading screen... then the screen flickers (out of sync?).  I then hear the nice startup music and I'm stuck.

I was able to use the vga=771 option and by using ctrl-alt-F1 got a text screen... partial success...

How can I change the screen resolution and restart xserver?

Thanks...
... stumped at midnight...

Hi,

Is your monitor connected to the GPU by means of the white digital connector? If so, and if it is possible of course, try the blue analog VGA connector. I had the same issue a while back until I finally found what was causing the problem.
Hope it works for you to.

---

### Post by pkarza on 2009-04-12
I'm using the VGA connector.  It works for XP using the same computer and it works.

I think it must be the monitor frequency setting or resolution.  I know that this TV only works with certain frequencies and resolutions.

What is the native resolution that ubuntu boots to?  How can I change this on startup with the live cd?

---

