---
title: "how to disable event sounds without gconf?"
date: 2009-05-01
forum: Desktop Environments
---

### Post by bareflix on 2009-05-01
I just upgraded to Jaunty, and now all my gnome applications beep when I click buttons, open windows etc. I know how to turn this off with gconf, but I don't run gconfd. I don't use the normal gnome desktop, just a few applications, and I prefer the "default" theme to what gconfd inflicts on me when I run it. As far as I can tell, there's no way to tell gconfd to not set a theme.

Anyway, after upgrading to Jaunty I now have this annoying beeping. Is there any way to turn it off in some default configuration that gets read before gconf?

I tried turning it off in gconf-config, and I see:
% gconftool-2 -R /desktop/gnome | grep sound
 /desktop/gnome/sound:
  input_feedback_sounds = false
  event_sounds = false
   command = sound-juicer %s

but this is ignored if gconfd is not running.

any suggestions appreciated.

--
Chris

---

