---
title: "Morrowind with Wine crash"
date: 2007-04-29
forum: Gaming &amp; Leisure
---

### Post by superbum on 2007-04-29
about the time I fill in a name on the ship in the begining and I get this in the terminal 

> Sorry, unknown layer type.
Not supported!
Stream error
err:dsound: DSOUND_MixOne underrun on sound buffer 0x1d81c10
mpg123: Can't rewind stream by 142 bits!
Sorry, unknown layer type.
big_values too large!
mpg123: Can't rewind stream by 870 bits!
big_values too large!
Can't step back 238!
big_values too large!
fixme:d3d:IWineD3DDeviceImpl_ResourceReleased Vertex buffer released while bound to a state block, stream 0

alot more before that too, but pretty repetitive, is there something I can do to get morrowind to work?

---

### Post by superbum on 2007-04-30
I've tried all the drivers and the ones that give me sound make it crash at the same place, I can play it with out sound but that kind of sucks, can anybody help me out?

---

### Post by lordhebe on 2007-04-30
Did you rename the MUSIC folder to something else? I had to do this to avoid a crash. The downside is that music won't run.

---

### Post by superbum on 2007-04-30
I did that and have no sound, and then it crashed when I went above deck, I've only tried once and I'll try again in a little bit.

---

### Post by Roostey on 2007-05-04
I had a similar problem - the game ran without sound until I tried to leave the ship when it crashed. 

 I fixed it by changing the audio settings in winecfg to match the comments posted Greg Schick on the Morrowind App DB page.

[http://appdb.winehq.org/appview.php?iVersionId=3329](http://appdb.winehq.org/appview.php?iVersionId=3329)

On the audio tab in winecfg, set the sound driver to ALSA, hardware acceleration to emulation, default sample rate to 22050, default bits per sample to 16.

---

