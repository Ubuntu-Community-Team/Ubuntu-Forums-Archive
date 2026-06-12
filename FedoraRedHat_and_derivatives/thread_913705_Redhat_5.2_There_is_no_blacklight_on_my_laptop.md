---
title: "Redhat 5.2 There is no blacklight on my laptop?"
date: 2008-09-08
forum: Fedora/RedHat and derivatives
---

### Post by worx101 on 2008-09-08
When it boots into a windows manager... the screen just goes extremely dark...

At first I thought it was just a black screen, but on closer inspection it appears to just be really dark.(no backlight)

Reset and go to command prompt and it's ok... just this way when running a windows manager...

Pretty sure there is a simple enough fix but I sadly do not know...

Any advice?  Thanks...

My notebook is a Compaq nc6400.

---

### Post by dca on 2008-09-08
Could be 'Power Management' issues.  RHEL5.x runs older kernel (2.6.18 which I believe is actually hybrid 2.6.17) missing a lot of features which 2.6.2x+ kernel offers...  Possible conflict if laptop has BIOS-based power management (look in BIOS for any screen settings).  The only time I've seen this was it being dim from running on battery, plugging in AC cable helped.  Check in 'System -> Preferences -> Keyboard shortcuts' and try and see if FN + Dimming keys set-up.

---

