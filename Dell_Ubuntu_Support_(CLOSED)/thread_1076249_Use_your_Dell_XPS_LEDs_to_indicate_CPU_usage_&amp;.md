---
title: "Use your Dell XPS LEDs to indicate CPU usage &amp; temperature"
date: 2009-02-21
forum: Dell Ubuntu Support (CLOSED)
---

### Post by DarthDogCow on 2009-02-21
In case anyone else is interested, I've put together a little daemon which changes the Dell XPS M1710 LED colour to indicate CPU load (green - amber - red) and temperature (blue - purple - red).  The zone LEDs used for each indicator can be configured.

"Why?" I hear you ask...

"So that I can keep an eye on my core usage & temperature when I'm playing full screen games, or encoding video with the lid closed." I reply.

Possibly not everyone's cup of tea, but you can grab a copy from Sourceforge:

[INDENT][**[COLOR="Blue"]http://sourceforge.net/projects/dellxpsled/[/COLOR]**]("http://sourceforge.net/projects/dellxpsled/")[/INDENT]
It's been tested on the M1710 running Intrepid 32-bit, but as it relies on libsmbios-bin it *should* work OK on any Dell XPS with LEDs which supports the libsmbios-bin package, running on any Ubuntu variant.

As a simple rule of thumb, if you can use [timovwb's XPS LED Changer]("http://sourceforge.net/projects/xpsledchanger/") GUI tool then this should work too.

Any feedback welcome :-)

Cheers,

Warren

---

