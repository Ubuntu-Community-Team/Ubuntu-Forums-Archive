---
title: "KDE apps no sound under GNOME (Feisty)"
date: 2007-04-03
forum: Desktop Environments
---

### Post by Shoubidouw@@@ on 2007-04-03
Hi,

I'm running Feisty heird 5 under GNOME.
I have problem using amarok or kaffeine...simply no sound comes out!!
Movie Player or Rythmbox play songs or movies without problem, i have the sound working fine with GNOME apps...

Can someone help me??

Thanks

---

### Post by louis_nichols on 2007-04-03
Did you set amarok to use alsa for sound output? That's how it should be. Setting this depends very little on whether you use amarok-xine or amarok-gstreamer. It's under Settings>Configure amarok>Engine. At this screen, it will be pretty obvious what you need to do. ;)

---

### Post by Shoubidouw@@@ on 2007-04-03
Thanks for your reply.... I found my problem...the onboard sound card on my mobo was not deactivated. I went into BIOS and deactivate it. Works fine now.

Thanks anyway.

---

