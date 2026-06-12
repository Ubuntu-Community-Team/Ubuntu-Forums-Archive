---
title: "treble/bass control"
date: 2005-03-26
forum: Desktop Environments
---

### Post by dlanor78 on 2005-03-26
In kmix I have sliders for adjusting bass and treble but they do nothing.  I have a creative soundblaster pci 512.  Is this sort of thing still done with emu-tools, or is there something I need to do in alsa?  Or is there another option these days?

TIA for any help.



[edit]
I did a bit more searching and I may have found the solution (but won't know if it's permanent until a reboot).  Here's what I did:

amixer sset Tone on (this made the bass/treble work)
sudo alsactl store (hopefully this will make the bass/treble still work after a reboot)

That's it :)  If there's anything that needs correcting, or any other steps that need to be taken, please don't hesitate to post it please.
[edit]

---

