---
title: "resolution"
date: 2007-09-25
forum: Desktop Effects &amp; Customization
---

### Post by haZZe08 on 2007-09-25
how do i enabel 1440x900 resolution?

i have a samsung syncmaster 940bw 19 in monitor


i have compizfusion on and my ati radeon graphics cardx700 pro in gnome with xgl

---

### Post by condamine on 2007-09-25
I've been down this road and let me tell you it is both very simple yet mind bogglingly complex at the same time.

Basically you must edit your /etc/X11/xorg.conf file to add the resolution you want.

There is a fair bit already written about this on the forums and in the community help area. Here are some links to the general how to's.
[ How to set you monitor resolution]("http://ubuntuforums.org/showthread.php?t=269052")
 [HOWTO: change resolution/refresh rate in Xorg]("http://ubuntuforums.org/showthread.php?t=83973")
[Screen Refresh Rate]("http://ubuntuforums.org/archive/index.php/t-186021.html")
[FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto#head-0e3051713171cb5d1bf49dc2dc7bea24eb9ed83e")

You could also search for your particular hardware items to see if someone has posted a xorg.conf file for your particular set-up.
You could also try a similar search at [Xorg-conf.org]("http://aleks.vigio.pl/?lang=eng&page=search")

---

