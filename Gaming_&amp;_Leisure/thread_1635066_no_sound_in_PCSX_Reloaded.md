---
title: "no sound in PCSX Reloaded"
date: 2010-12-01
forum: Gaming &amp; Leisure
---

### Post by kistina on 2010-12-01
I suddenly have no sound in PCSX Reloaded no matter what game I try, I had been using it for a couple of days and it was working fine up until now (though the sound was a bit choppy some times).  There are no errors when I run it in the console and running it with padsp like another thread suggested did nothing. I am using Ubuntu 10.10.

---

### Post by thatguruguy on 2010-12-01
> **kistina said:**
> I suddenly have no sound in PCSX Reloaded no matter what game I try, I had been using it for a couple of days and it was working fine up until now (though the sound was a bit choppy some times).  There are no errors when I run it in the console and running it with padsp like another thread suggested did nothing. I am using Ubuntu 10.10.

Which sound plugin are you using?  
Which version of pcsx-r are you using?
Do you have sound in other applications?

---

### Post by kistina on 2010-12-01
oh, sorry I forgot to give that info. Should have thought of that.
  
Plugin: "SDL Sound 1.6.0" (plugin that came with it, have tried the "pete's" plugins after, but they didn't work either)
Version: 1.9.92

After my last post I have tried epsxe with some hassle and it wouldn't do sound either.  Also sound does work in all other applications.

---

### Post by thatguruguy on 2010-12-01
Strange. I'm using SDL Sound 1.6.0, as well.  What's your configuration on that plugin?

I have:
Volume: Loud
Reverb: Playstation
Interpolation: Gaussian
Adjust XA Speed is unchecked
High compatibility mode is checked
SPU IRQ Wait is checked
Single channel sound is unchecked.

---

### Post by kistina on 2010-12-01
Volume: Loudest
Reverb: Playstation
Interpolation: Gaussian
Adjust XA Speed: Checked
High compatibility mode: Unchecked
SPU IRQ Wait: Checked
Single channel sound: Unchecked

and tried your setup just to see and still no sound

---

### Post by kistina on 2010-12-01
Ok, now I have figured out that the problem is not with PCSX, I figured out that most of the other applications were using alsa, when switching my music player to Pulse Audio it stopped playing, Pulse Audio is installed though.

---

### Post by kistina on 2010-12-01
under even further investigation I went and looked at the devices tab on the pulseaudio manager and it says
Sinks
   auto_null    Dummy output
Sources
   auto_null.monitor   Monitor of Dummy Output

I am guessing that means that for some reason it isn't configured to use my soundblaster card, how can I fix this?

---

### Post by kistina on 2010-12-01
oddly enough the problem sorted it's self out, I restarted and everything is working fine again

---

### Post by thatguruguy on 2010-12-01
Good!  Pulse can be kinda touchy at times. Glad it worked itself out.

---

