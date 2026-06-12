---
title: "Rolling back updates?"
date: 2008-08-18
forum: Dell Ubuntu Support (CLOSED)
---

### Post by secristrc on 2008-08-18
Where is the log of most recent things changed by the Update Manager, and is there any way to roll those changes back?

I had a few updates I hadn't applied lying around in the Update Manager, and finally gave into it, but my volume control was immediately busted by them, and I want to roll back.  Am I toast?

I'm a 1525N running the 7.10 under Gnome.  I get a tiny bit of motion out of the buttons or the slider, and can still mute, but that is it.

Thanks!
rcs

---

### Post by ms_whosit on 2008-08-18
This happened to me when I updated from kernel 2.6.22.14 to 2.6.22.15. I can boot from the old kernel (change it in the Grub menu), and then the microphone, soundcard/alsa, and volume control all work fine. Was yours a kernel update? Can you try booting from the old kernel in Grub?

But I usually use the newer kernel if I don't want to use the sound card, because I figure it's more secure. Anyone else have an opinion?

---

