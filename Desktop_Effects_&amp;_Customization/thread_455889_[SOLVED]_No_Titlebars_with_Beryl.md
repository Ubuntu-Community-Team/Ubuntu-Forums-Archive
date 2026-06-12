---
title: "[SOLVED] No Titlebars with Beryl"
date: 2007-05-27
forum: Desktop Effects &amp; Customization
---

### Post by Beatbreaker on 2007-05-27
hey i've lost my title bars in Beryl. It was working perfectly and then one day (now) i don't have title bars - no maxamise, minimise bars etc.... 3d desktop still works along with other things, just no title bars has made it very hard to use


- i've tried heaps of things, i've got the window decorator enabled and i've loaded, do you think i've hade a change in emerald?

even if i change to compiz i don't have title bars, only if i switch to Metacity will i get them back. 

what have i done?

is it possible i can just uninstall it completely and reinstall with all default preferences?

...actually that may be something for the developers to consider - there might have to be a "revert to default" settings button to help all us num nuts out there if we make changes we can't remember in Beryl

many thanks guys!

---

### Post by Cresho on 2007-05-27
sudo gedit

/etc/X11/xorg.conf in the “Device” section: add the following in this section

Option         "AddARGBGLXVisuals" "True"
Option         "RenderAccel" "True"
Option         "AllowGLXWithComposite" "True"
Option         "backingstore" "True"
Option         "TripleBuffer" "True"

---

### Post by Beatbreaker on 2007-05-27
thankx for the speedy reply and sorry to waste your time, i read this thread and found the answer:

[http://ubuntuforums.org/showthread.php?t=307530](http://ubuntuforums.org/showthread.php?t=307530)

this thread may now be locked

---

