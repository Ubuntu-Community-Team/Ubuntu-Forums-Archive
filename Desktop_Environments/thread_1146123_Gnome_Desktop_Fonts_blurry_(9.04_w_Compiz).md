---
title: "Gnome Desktop Fonts blurry (9.04 w/ Compiz)"
date: 2009-05-02
forum: Desktop Environments
---

### Post by chocobanana on 2009-05-02
Greetings

For some weird reason, Gnome with Compiz enabled on Ubuntu 9.04 starts with fonts rendered blurry. It used to render fonts just fine until I blacklisted some modules and updated initramfs to put this into effect.

After reverting the modules blacklist back to the previous settings, the problem still persists.

One temporary fix I found is to disable Desktop effects and re-enable it right after. This will make fonts render well again using Compiz. The problem is that this solution does not survive a reboot.

Can somebody help?

Thanks :)

---

### Post by dsavi on 2009-05-02
You're almost there. Check in the compizconfig settings manager (Can't remember the command to get it sorry) for the "Blur windows" plugin under Effects and disable it. This happened to me once and I thought I was going crazy.

---

