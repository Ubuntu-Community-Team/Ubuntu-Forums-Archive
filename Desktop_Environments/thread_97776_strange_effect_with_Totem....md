---
title: "strange effect with Totem..."
date: 2005-12-01
forum: Desktop Environments
---

### Post by bonsiware on 2005-12-01
I've been running breezy with ATI drivers 8.19.10 for a few days without problems, and I know that, to let totem work fine with fglrx, I have to add:

```

	Option 		"VideoOverlay" 		"on"
	Option 		"OpenGLOverlay" 	"off"
	Option 		"UseInternalAGPGART" 	"no"

```

...in the device section of xorg.conf...

but today, playing my favourite climbing videos, I have a strange 'pixelated' effect... it seems that the video resolution is low, it's not smooth... 

mplayer and vlc still work fine...

any idea?

---

