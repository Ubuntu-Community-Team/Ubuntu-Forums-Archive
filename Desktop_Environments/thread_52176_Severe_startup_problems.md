---
title: "Severe startup problems"
date: 2005-07-26
forum: Desktop Environments
---

### Post by Aragorn992 on 2005-07-26
I (yes I know im stupid but I just wanted decent movie playback) force installed totem-xine with:

dpkg -i --force-all totem-xine

And totem-gstreamer was removed (which I presume Nautilus and/or Gnome uses).

Now when I startup I get the following error messages repeatedly:

-gnome-panel has quit unexpectedly
-nautilus has quit unexpectedly

When ever I clock restart, or close or whatever, they just keep coming up.

Im guessing I need to reinstall totem-gstreamer?

Any help appreciated.

---

### Post by ubuntp on 2005-07-26
Neither of them use totem-gstreamer, only totem uses it. Also when you install totem-xine, totem-gstreamer is uninstalled automatically and in a clean way, so why did you had to --force-all anyway?

---

