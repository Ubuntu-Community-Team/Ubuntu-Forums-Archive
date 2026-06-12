---
title: "ltsp client resolution"
date: 2006-10-08
forum: Desktop Environments
---

### Post by Tim Sawyer on 2006-10-08
Hi,

I've sucessfully set up edubuntu (6.06) as an ltsp server, with a single client.  The server has two monitors, and works fine with both at 1280x1024.  The client has a similar monitor which used to (under gentoo ltsp before I saw the light) work fine at 1280x1024.  The client seems to be stuck at 1024x768 and I can't get it to go any higher.  Can anyone point me in the right direction?

lts.conf just has the following in:

[default]
  SOUND = true
  XSERVER = nv
  X_COLOR_DEPTH = 16
  SYSLOG_HOST = 192.168.1.14
  XKBMODEL = gb

and /opt/ltsp/i386/etc/X11/xorg.conf has:

SubSection "Display"
  Depth           16
  Modes           "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection
  SubSection "Display"
  Depth           24
  Modes           "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection

in the screen section.

Any pointers would be appreciated, I've found it hard to get documentation on edubuntu's ltsp setup.

ta,

Tim.

---

### Post by Kalif on 2006-12-07
OK, you are running dapper, that is good, regarding documentation,
because it is more like the original implementation at ltsp.org:
then you should be able to set

X_MODE_0 = 1280x1024

in your lts.conf
another point to mention is that your monitor may not
be plugging and playing as it should which may convince
client that your monitor is not good for more than 1024x768.
On the other hand it may not be, even if it seems to be
running good at 1280x1024; check with the manual, if we
are talking about CRT:s (and not modern TFT (thin) monitors)
the vertical sync pulse is then used for genereation of
the high voltage for the acceleration. In that case the
monitor may work fine, but it will probably die a little
bit early, which may be fine if you are planning on buying
a proper TFT 8-)

Good luck,
K.

---

