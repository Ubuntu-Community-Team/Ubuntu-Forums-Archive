---
title: "No system sound in Unity"
date: 2013-11-19
forum: Desktop Environments
---

### Post by molgrum on 2013-11-19
Hello everyone.

I used Gnome Shell for quite some time instead of Unity and in X-Chat I could hear a "thud" sound whenever my nick is highlighted. However now since I switched back to Unity that sound doesn't play at all.
I'm puzzled about this because sound works on every app I launch. So I went to the Sound app to figure things out and in the "sound effects" tab I noticed the alert volume was all the way to zero, so I reversed it all the way to 100 percent but it didn't solve anything.

Now I'm fresh out of ideas about this problem and I need help.

---

### Post by fantab on 2013-11-19
Deleted: OP has already tried it.

---

### Post by molgrum on 2013-11-20
Freshly upgraded from 13.04 to 13.10, still the same problem. No system alert sounds play in Unity.

---

### Post by molgrum on 2013-11-21
I tried invoking the GNOME Control Center by commandline and as soon as I clicked the "sound" icon this text was in the output:

```
~$ gnome-control-center 
*** BUG ***
In pixman_region32_init_rect: Invalid rectangle passed
Set a breakpoint on '_pixman_log_error' to debug


(gnome-control-center:4092): sound-cc-panel-WARNING **: active_output_update - couldn't find a stream from the supposed active output

(gnome-control-center:4092): sound-cc-panel-WARNING **: active_input_update - couldn't find a stream from the supposed active input
```

Maybe someone knows if I can check a log file for errors?

---

### Post by molgrum on 2013-11-23
I tried a few other DEs, Cinnamon and GNOME Fallback. Cinnamon has the sound but GNOME Fallback doesn't.

---

### Post by molgrum on 2013-11-27
[http://www.omgubuntu.co.uk/2013/04/how-to-reset-unity-compiz-in-ubuntu-12-10-and-13-04](http://www.omgubuntu.co.uk/2013/04/how-to-reset-unity-compiz-in-ubuntu-12-10-and-13-04)
I tried resetting Unity with step 1 here, no success.

---

