---
title: "snes emulation problems"
date: 2006-08-02
forum: Gaming &amp; Leisure
---

### Post by slimdog360 on 2006-08-02
Im trying to play chrono trigger and I have problems wih th emulation. Ive tried both snes9x and zsnes but have problems with both of them. Using zsnes its a bit jumpy when just walking around. Under snes9x it runs fine apart from the fact that there is no sound. 
When I try them both using kde I get the same problem with zsnes but with snes9x everything runs fine. This would be alright but since I prefer using gnome it gets annoying when wanting to run other things at the same time.
  I suppose it would be easier to get the sound working with snes9x because it works with kde.
Can anyone help???
thanks.

---

### Post by frup on 2006-08-02
probably not as roms are illegal... also maybe if you are really worried etc.. a better place would be to ask the snes9x/zsnes developers

---

### Post by slimdog360 on 2006-08-02
> **frup said:**
> probably not as roms are illegal... also maybe if you are really worried etc.. a better place would be to ask the snes9x/zsnes developers

unless I own the original cartridge, which I do. I want to run it on the computer because my snes it broken, also I can take it ith my on my laptop.

---

### Post by radiazo on 2006-08-09
> **slimdog360 said:**
> Using zsnes its a bit jumpy when just walking around. 
That depends of your hardware configuration. What video card and what drivers are you using?
> **slimdog360 said:**
> 
Under snes9x it runs fine apart from the fact that there is no sound.
maybe snes use dsp directly. try to install alsa-oss and after run in console  "aoss snes9x"

---

### Post by adamward on 2006-08-09
> **slimdog360 said:**
> unless I own the original cartridge, which I do. I want to run it on the computer because my snes it broken, also I can take it ith my on my laptop.

Not to be nitpicky, but that is not accurate if you live in the United States.  Here, even if you own the cartridge, you can not legally have a rom image, even for 24 hours as some sites state.  Granted, I think that's stupid, and if the game is not in production, then just release the rom, especailly since it's that old of a game.

Anyways...like you, I prefer gnome, and the alsa-oss trick did not seem to help me, but I'm running on an HP nc6120 laptop, so I don't expect a lot of things to really function correctly, being a laptop and all.

--adam

---

### Post by radiazo on 2006-08-09
snes9x uses the oss lib. Is possible to use it with alsa-oss and a modifier:

"aoss snes9x -r 7 *rompath*" this resample the sound at 44000 hz.
and for zsnes, use the video settings on "800x600 ODS FULL", using the opengl renderer.
if you have problems tell me.
cheers,

Ronald

---

