---
title: "desktop effects could not be enabled , openchrome driver"
date: 2007-10-30
forum: Desktop Effects &amp; Customization
---

### Post by ronenmv on 2007-10-30
Hello

I'm using ubuntu 7.10, I have via/s3 graphic drive and I'm using the openchrome driver.

when trying to enable normal visual effects I get this error "desktop effects could not be enabled"
when typing compiz in terminal I get this :

Checking for Xgl: not present. 
No whitelisted driver found
aborting and using fallback: /usr/bin/metacity 

can I enable effects with my hardware??
please help me
thank you.

---

### Post by Forlong on 2007-10-30
> **ronenmv said:**
> can I enable effects with my hardware??
Sorry, you can't:
> To run the new fancy compositing desktops that use OpenGL as a backend, you will need extensions and features that are not yet supported in the unichrome 3D driver. This includes, among other things, support for big textures and some blitting functions that are not yet accelerated. Efforts are underway in the DRI project (initially with the i915 driver) to create a general memory manager infrastructure on top of which these things can be built, but it will take quite some time before these things can be implemented in the unichrome 3D driver. Mainly because there is no maintainer of the driver.
[http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=3DStatus](http://wiki.openchrome.org/tikiwiki/tiki-index.php?page=3DStatus)

---

