---
title: "xscreensaver starts while watching youtube in firefox 14.04"
date: 2015-07-31
forum: Desktop Environments
---

### Post by coljohnhannibalsmith on 2015-07-31
Hello,

While watching YouTube in Firefox xsreensaver starts.  I've experienced this in other distros, but never
in 14.04 until now. If xscreensaver were not installed, I believe the screen would have just blanked, as
in many previous distros. I thought this problem had been licked. Will I have to write a shell script to
ping the OS, just to keep the screensaver from starting or the screen from blanking?

Thanks, Hannibal

---

### Post by Dennis N on 2015-07-31
You can disable xscreensaver in its settings dialog. Settings > Xscreensaver > Display Modes Tab > Mode = Disable Screensaver. Then it will not come on during your video.

---

### Post by coljohnhannibalsmith on 2015-07-31
I'm not finding this path. I'm in a Flashback Compiz session. Things might be organized a little differently here.
Also, why should I have to do this; is there no communication between xscreensaver and the OS?

Thanks, Hannibal

---

### Post by Dennis N on 2015-07-31
I'm not using Gnome Flashback, so that my take some hunting about on your part. There has to be a settings dialog on there somewhere for xscreensaver, I would think.

---

### Post by coljohnhannibalsmith on 2015-07-31
I've checked the advanced settings in xscreensaver itself; and there does not appear to be an option
to disable xscreensaver.

Thanks, Hannibal

---

### Post by coljohnhannibalsmith on 2015-08-01
Apparently, there's a problem with this package:

xserver-xorg-core-lts-utopic2:1.16.0-1ubuntu1.2-trusty2

Please see the attachment.

BTW, I counldn't send the report because of the crash.  Also, this tool would be a lot easier to use if it
has the Edit > Select All option like Terminal does.

---

### Post by coljohnhannibalsmith on 2015-08-01
> **Dennis N said:**
> You can disable xscreensaver in its settings dialog. Settings > Xscreensaver > Display Modes Tab > Mode = Disable Screensaver. Then it will not come on during your video.

BTW, I finally found this setting in System Tools > Preferences > Screensaver > Mode > Disable Screensaver

I'll try this awhile to see if it works; but I shouldn't have to do this.  XScreensaver should listen to the data
stream and determine if there's a media file playing; and there should be two options; 1 to not have the screensaver
start if there is a media file playing, 2 To allow the screensaver to start, if there's no keyboard or mouse activity.
That way if I walk from my pc in an unsecure place, the screensaver will start to hide my work and lock the
screen.

Hannibal

---

