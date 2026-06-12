---
title: "[SOLVED] Changing themes from a script?"
date: 2006-07-26
forum: Desktop Environments
---

### Post by KevinRJohnson on 2006-07-26
Hey all,

How would I change the desktop theme in a script?  

I'm an amateur astronomer and I would like to use my laptop at the observatory alongside the telescope, however a bright nice theme for use during the day destroys your nightvision.  I've figured out how to use nvidia-settings to tone down the brightness and set my display to show in red only.  I even have all the stuff needed to do this in a script.  Now if I could just get it to switch between themes so I could use a theme that is good for working on my machine during the day, and when I hit the observatory at night switch to a theme that's more well suited for that purpose that would be awesome.  Any ideas on how I would do this?

Thanks,
Kevin R. Johnson

---

### Post by KevinRJohnson on 2007-07-19
I found that using the nvidia-settings program to manually set the green and Blue channels to zero intensity (completely off) works fantastically.  I even mad a little script to swap the two config files on command

NightVision:
```

#!/bin/bash
cp ~/.nvidia-settings-astro ~/.nvidia-settings-rc
nvidia-settings --load-config-only
#rm ~/.icons/default
#ln -s ~/.icons/default_night ~/.icons/default
#gconftool -t str -s /desktop/gnome/peripherals/mouse/cursor_theme "default"
#gconftool -t str -s /schemas/desktop/gnome/peripherals/mouse/cursor_theme "default"

```

DayVision:
```

#!/bin/bash
cp ~/.nvidia-settings-normal ~/.nvidia-settings-rc
nvidia-settings --load-config-only
#rm ~/.icons/default
#ln -s ~/.icons/default_day ~/.icons/default
#gconftool -t str -s /desktop/gnome/peripherals/mouse/cursor_theme "default"
#gconftool -t str -s /schemas/desktop/gnome/peripherals/mouse/cursor_theme "default"

```

You have to make the config files and place them manually though.

Hope that helps!

Kevin

---

