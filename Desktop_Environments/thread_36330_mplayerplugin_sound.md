---
title: "mplayerplugin sound"
date: 2005-05-22
forum: Desktop Environments
---

### Post by art on 2005-05-22
Hi forum
Anyone has success with mplayerplugin and quicktime movies sound? I can watch movie trailers on apple.com but no sound ](*,) . Any ideas?
Thanks a lot.

---

### Post by Knome_fan on 2005-05-23
1. Make sure you have the w32codecs package installed:
[http://www.ubuntuguide.org/#codecs](http://www.ubuntuguide.org/#codecs)

2. Make sure that mplayer uses esd. Put:
ao=esd
into ~/.mplayer/config

---

### Post by art on 2005-05-23
Great!
Thanks a ton

---

### Post by wazoo on 2005-05-23
Hmm, I'm baffled. In Warty, I had sound and such. After the upgrade I lost the ability to play trailers again.

I've restored mplayer, and can watch the video, but no sound. When I go to mplayer and try to choose esd out -- there IS no esd!

I've removed and restored, and deleted my old ~/.mplayer directory, but no joy. The esd daemon is running.

Suggestions?

---

