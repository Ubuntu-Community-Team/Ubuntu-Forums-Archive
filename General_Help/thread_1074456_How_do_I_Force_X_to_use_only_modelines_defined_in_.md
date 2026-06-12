---
title: "How do I Force X to use only modelines defined in xorg.conf"
date: 2009-02-19
forum: General Help
---

### Post by fatski on 2009-02-19
Had a quick search around the forum for a solution to this one, but no luck. It's really more of an annoyance than a showstopping problem, but any help would still be appreciated.

I have my Ubuntu laptop connected to a 1080p Samsung TV. The only two useful resolutions for this are 1360*768 & 1920*1080 and I have working modelines for these in my xorg.conf. I would like to use something like krandrtray to quickly switch between these two resolutions, however every app that allows switching of resolutions, from ATI Catalyst Control Panel to xrandr, is populated with about 20 different resolution options that my TV just cannot display, stuff like 320*200 and 1440*900.

At a guess I'd say these are standard VESA resolutions that Xorg thinks my TV should be able to display, even though I haven't defined them. So my question is, does anybody know of a way to force X to only consider resolutions explicitly defined in xorg.conf and ignore everything else, like built in VESA modes?

Thanks in advance.

---

### Post by dcstar on 2009-02-19
> **fatski said:**
> Had a quick search around the forum for a solution to this one, but no luck. It's really more of an annoyance than a showstopping problem, but any help would still be appreciated.

I have my Ubuntu laptop connected to a 1080p Samsung TV. The only two useful resolutions for this are 1360*768 & 1920*1080 and I have working modelines for these in my xorg.conf. I would like to use something like krandrtray to quickly switch between these two resolutions, however every app that allows switching of resolutions, from ATI Catalyst Control Panel to xrandr, is populated with about 20 different resolution options that my TV just cannot display, stuff like 320*200 and 1440*900.

At a guess I'd say these are standard VESA resolutions that Xorg thinks my TV should be able to display, even though I haven't defined them. So my question is, does anybody know of a way to force X to only consider resolutions explicitly defined in xorg.conf and ignore everything else, like built in VESA modes?

Thanks in advance.

I believe that there is an xorg.conf option called "edid" that you can turn off to stop fetching resolutions from the hardware, a search should provide more details.

---

