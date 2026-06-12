---
title: "Live CD awn-compiz"
date: 2007-11-15
forum: Desktop Effects &amp; Customization
---

### Post by rpk5000 on 2007-11-15
(Sorry if this is the wrong forum, move it if it is)

Is it possible to get Ubuntu 7.10 to run awn without installing (from a live cd)?

When I attempted to start awn, I got the compiz is not enabled error.  I have an nVidia 7600 so it should support compiz.  However, when I enabled the graphics card driver in the restricted libraries, the cd prompted me to restart.  Obviously, this would kill the graphics driver so instead I chose to restart x.  I switched to the alt-F1 console and killed all processes and stopped X.  However, when I tried to restart X I got a weird error asking about my broadcom wireless driver (I think that was it), I have a linksys card (WMP54GS), and its unsupported, so I bridged a connection from a windows machine that did have access over an Ethernet cable so eventually I would be able to download awn.  I never actually unplugged my card (I have to keep my Vista installation intact as much as possible - I'll switch to Ubuntu when it supports Photoshop properly)

After that I tried a number of things to allow persistence with a usb flash drive, none of which aparently worked.  I also tried installing linux to the flash drive and doing persistence that way (both of the persistent usb things I followed the Ubuntu docs for as well as trying an alternate method posted online).

Finally, I tried using VMwares player to run compiz, but the graphics card (VMware Virtual Graphics card) is incapable of running compiz.

What's the best way to get awn to run without damaging my current installation of Vista?

Thanks

Misc Info (Ubuntu 7.10, 2 gigs of ram, Pentium D not oc, nVidia 7600)

---

### Post by Honkboy on 2007-11-16
To enable the restricted drivers you have to restart your system... so the only possible way to get them working is to implement them into your own live cd build
there is a project working on that (though I haven't tried it out yet)
[http://uck.sourceforge.net/]("http://uck.sourceforge.net/")
maybe that helps

---

### Post by rpk5000 on 2007-11-17
Is there no other way to do it?

Obviously I would prefer a virtual solution, but is it possible to accomplish this with persistence?

---

