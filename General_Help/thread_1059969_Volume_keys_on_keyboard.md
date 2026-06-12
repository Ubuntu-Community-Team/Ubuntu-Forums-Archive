---
title: "Volume keys on keyboard?"
date: 2009-02-04
forum: General Help
---

### Post by gbrethen on 2009-02-04
New to Ubuntu, so bare with me....

When I press the function + volume up keys, the volume doesn't change but the volume graphic pops up on the screen and shows the adjustment, but the volume control in the system tray doesn't move?  is there a solution to this?

Thanks

---

### Post by gbrethen on 2009-02-04
found some forums with similar issue.  Has there been a fix for this yet?

---

### Post by gbrethen on 2009-02-04
I solved my problem by changing the Device Mixer in the sound settings.  I also Changed from ALSA to PulseAudio Sound Server.  After doing that, now my volume and mute keys work.

Hope this helps others.

---

### Post by prkos on 2009-02-06
Thank you, I had the same problem and solved it by changing the setting Device: under System > Preferences > Sound. It was set to Capture:blah, I changed it to Playback:blah, using Pulse of course.

---

