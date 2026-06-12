---
title: "No Sound at all!"
date: 2005-10-17
forum: Desktop Environments
---

### Post by MAMOHT on 2005-10-17
Strange things happened when I upgraded Hoary to Breezy. Everuthing was ok, the upgrade procedure went normal, but after that the sound has gone!! I also try to play any mp3 and it sais to me that no codec can be found to decode the stream!
What happened?

---

### Post by Dr. Nick on 2005-10-17
You have no sound anywhere? Post what kind of soundcard you have and check ```
lsmod
``` for any mention of your card. If you get that the codecs should be as easy as enabling usinverse and installing the gstreamer codecs

---

