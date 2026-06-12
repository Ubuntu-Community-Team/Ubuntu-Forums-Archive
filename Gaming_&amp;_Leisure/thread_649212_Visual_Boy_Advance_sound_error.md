---
title: "Visual Boy Advance sound error"
date: 2007-12-24
forum: Gaming &amp; Leisure
---

### Post by BenTyrer on 2007-12-24
Hey everyone, this is my first post, and I'm a bit of an Ubuntu newbie as I've only had it running on my pc for a few weeks; really, really love it though.

I'm having some problems getting the VBA emulator running smoothly, however.

I've downloaded The windows version, and I'm running it through wine,
When I load a ROM, I get an error saying
"Cannot Create Directsound 00000001" and then the game runs at unusually high speeds.


I've tried tinkering around with various settings on vba, but nothings worked. I've also unchecked the setting 'Enable software sound mixing (ESD)' in System>Preferences>Sound but that's done nothing to help.

Could anyone suggest any fixes for this, preferably step-by-step so a newbie like me can follow? :)

And If worst comes to worst, can someone tell me how to get 'mednafen' working, as I've heard from other posts it works without problems, though I'm not certain how to set it up.

thanks to any replies in advance,
Ben.

---

### Post by DjBones on 2007-12-25
have you tried VBA natively?
you can install without wine by typing into a terminal:
```
sudo apt-get install visualboyadvance visualboyadvance-gtk
```

or to install mednafen type into a terminal:
```
sudo apt-get install mednafen
```

even then, the sound is still a little sketchy for myself..

---

### Post by BenTyrer on 2007-12-25
Thanks for the reply, although that didn't seem to do the trick;

Never mind though, I would of liked to play some retro roms, but I guess I can come back to this later, when it is well documented enough to allow me to fix this problem.

---

