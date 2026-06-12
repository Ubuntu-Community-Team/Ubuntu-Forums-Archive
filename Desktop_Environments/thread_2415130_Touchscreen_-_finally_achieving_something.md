---
title: "Touchscreen - finally achieving something?"
date: 2019-03-20
forum: Desktop Environments
---

### Post by udippel on 2019-03-20
I've been a *nix user for more than 20 years, and finally ended with a convertible. To my surprise, this is currently much less supported than I had hoped. Of course, the basics work pretty okay. But not even right click is available. 
Now I am looking for some support, and will gladly report back and test modifications and improvements.

Some major still existing problems:

- It seems there is no built-in method to use the detector for tablet/keyboard mode, in order to switch to different desktop features, like auto-hide of panels.
- How do I intercept the Windows-logo-touch effected by touching the respective logo on the bezel (the touch feedback, vibration, does occur)
- The settings screen needs an extra input category for touchscreens
- The widths of scroll bars must be adaptable for smaller screens with higher resolutions, respectively imprecise touches through finger input
- The screen keyboard for logins must be correct, to allow authentication through that keyboard (already filed as bug)
- Working A LOT with edge events, the edge detection must also reliably work at moving finger or pen across the screen over the edge. Currently this is not the case. 
- The four 'touch-screen events' in the settings (gestures) do not work
- (As mentioned above,) the right click must be implemented; at least through a relative long time of touching a point (like in Windows)

I think, these eight would be a good starting point. Maybe one or another can already be achieved, and I appreciate any hint on the How-To.

Kind regards,

Uwe

---

