---
title: "gdm fails, can't recognize PNG images (Ubuntu 6.10)"
date: 2008-02-20
forum: Desktop Environments
---

### Post by Misheliskus on 2008-02-20
I've been running 6.10 on my laptop for about a year, but now I'm having problems with the Gnome GUI. When I boot up, I get the error:
[COLOR="Red"]There was an error load the theme Human
Couldn't recognize the image file format for file '/usr/share/gdm/themes/Human/background.png'[/COLOR]

It then loads the "standard greeter," I am able to log in but then pretty much everything that tries to run crashes, as far as I can tell due to problems loading image files. Dropping down to the terminal, I've tried various things with no success.

'file' recognizes background.png as "PNG image data, 1600x1200, 8-bit/color RGB, non-interleaved". Permissions look fine, anything can read it. fsck turns up nothing. I've tried dpkg-reconfigure on various things (libpng, ubuntu-minimal, ubuntu-standard, ...) but the only noteworthy behaviour is when I try to reconfigure gdm:

```

$ sudo /etc/init.d/gdm stop
  * Stopping GNOME Display Manager...
$ sudo dpkg-reconfigure gdm
  * Reloading GNOME Display Manager configuration...
  * Changes will take effect when all current X sessions have ended.
[COLOR="Red"]invoke-rc.d: initscript gdm, action "reload" failed.[/COLOR]

```

Removing and reinstalling gdm still gives the same problems and [COLOR="Red"]action "reload" failed[/COLOR] error, as does 'invoke-rc.d gdm reload'. I also tried 'invoke-rc.d gdm force-reload' but it made no difference.

I can't think of anything unusual I installed or did before these problems came up. I upgraded to the latest kernel a couple days ago, but that didn't cause any immediate problems. I'm running out of ideas, any advice would be greatly appreciated.

---

