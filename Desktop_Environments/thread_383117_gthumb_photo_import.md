---
title: "gthumb photo import"
date: 2007-03-12
forum: Desktop Environments
---

### Post by rogue_ronin on 2007-03-12
Hi!

I'm running Edgy, and I seem to have lost access to my digital camera.  It is a permissions problem, as I get a "you don't got no stinkin' permission" message when I press the button on my Kodak DX6440 dock.

This worked well up until very recently. I seem to recall a libgphoto update, don't I?

Owner of the USB port is root.  If I change owner to my username with chown, I can import the photos.  Is this a known bug?  Does anyone want to report it?  I find the whole bug-reporting thing kind of confusing, I'm afraid.

Has anyone got a suggestion for a configuration file edit?  I'm guessing this is libgphoto or HAL based.

Thanks!

m a r

---

### Post by rogue_ronin on 2007-03-13
It's the 2.3.0 backport of libgphoto2.

I rolled it back to 2.2.1 and problem gone.

m a r

ps: use the Force Version entry in the Package menu for Synaptic to pick the version you want.

---

