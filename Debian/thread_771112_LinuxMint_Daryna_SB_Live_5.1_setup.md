---
title: "LinuxMint Daryna SB Live 5.1 setup"
date: 2008-04-27
forum: Debian
---

### Post by prodigy6630 on 2008-04-27
Mint Newbie: I'm using LinuxMint Daryna which is based on Ubuntu 7.10 Gutsy Gibbon. How do I get my 5.1 surround working properly? 

I have a Sound Blaster Live 5.1 Digital. Mint installs an SB Live 5.1 [SB0220] (Alsa mixer) driver which does not work well. It has this blowing noise over the speakers which sounds terrible.

Are there alternate drivers I can use and if so, where do I get it and how do you install it.

Thanks :KS

---

### Post by frandy on 2008-04-30
Same problem here with Ubuntu 8.04.

Same card, same drivers. All I hear is hiss.

I checked alsamixer - all unmuted and levels up.

Any suggestions?

Thanks

---

### Post by reos2day on 2008-04-30
I have the Audigy SE card and in the ALSA Mixer I muted (using "M" key) the Audigy Analog/Digital Output Jack.  That got my 5.1 card playing stereo.  No surround yet, but good to have stereo at least.

---

### Post by tibellus on 2008-05-02
reos2day, you're a genius:guitar: I had the same problem with my SB Live! on a 5.1 system. Everything sounds great now:) I looked for the Analog/Digital Jack option, found it and muted it. Awesome! My thanks go to you!

---

### Post by frandy on 2008-05-13
yep!

Analog/Digital Jack option - changed status in GUI version of alsamixer

worked

sorted 

Thanks

---

### Post by Sef on 2008-05-13
Moved to Debian Linux or alternatives forum (excluding Ubuntu.)

---

