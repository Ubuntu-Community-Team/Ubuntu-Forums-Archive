---
title: "Screeching sound with Wine and WoW"
date: 2007-05-20
forum: Gaming &amp; Leisure
---

### Post by Mr_Sanderson on 2007-05-20
Hi guys I am having trouble getting quality sound when running WoW through Wine.  I had it working great at one point but when I installed Ventrilo my sound started popping and chirping/screeching from time to time.  The sound through vent is worse adding in more frequent chirps/screeches coupled with static.

Specs:
AMD 64
Ubuntu Fiesty 7.04
Wine 0.9.33
SB Live 5.1

What I have tried:
*SET SoundBufferSize "70"
*Tried OSS and ALSA settings in winecfg
*checked/unchecked driver emulation
*Direct sound Hardware Acceleration set to Emulation (have tried all of the others)
*22050 Sample Bit Rate
*8 bits per sample
*installed per [This Wiki]("http://www.wowwiki.com/Linux/Wine")

I don't mind if vent isn't running I'd just like to be able to play with some sound, any ideas on how to fix this?  Any help is much appreciated.

---

### Post by hikaricore on 2007-05-20
Yea... umm.... you did disable direct sound in ventrilo, right?  Because that really screws with wine pretty bad.

There's a vent howto around the forums somewhere, check to see if you've overlooked anything that might clear up your sound issues.

---

### Post by Mr_Sanderson on 2007-05-21
Problem Solved.

Thanks, I had disabled Input device DirectSound but missed the output device. I also bumped buffer up to 100 and everything works now.  Thanks again

---

### Post by hikaricore on 2007-05-21
:) Np this drove me batty on my girl's system until I figured out she kept accidently switching it back on.  ^_^

Sorry for being so vague and grumpy earlier, my pizza was late and I was taking out on t3h interwebs.  >.<

---

