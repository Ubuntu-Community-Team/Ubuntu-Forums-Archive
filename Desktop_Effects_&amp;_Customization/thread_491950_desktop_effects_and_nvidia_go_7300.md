---
title: "desktop effects and nvidia go 7300"
date: 2007-07-04
forum: Desktop Effects &amp; Customization
---

### Post by mokojin on 2007-07-04
Hi guys I just installed ubuntu 7.04 on my fresh laptop, and for the first time i can get all those nice effects that i see on youtube videos.

So.. regarding this i have some questions, since this is new to me.

my card is a Nvidia Go 7300

After install and update, i tried to enable Restricted Drivers to support the desktop effects (because i get a black screen on them) and the system responds that my hardware don't need restricted drivers.

Is this the normal procedure? should i install the drivers from nvidia site, beside the desktop effects i need 3d acceleration for my opengl games on wine.

some enlightenment on this would be appreciated, thanks

PS: does desktop effects and opengl games give along well?

---

### Post by renzokuken on 2007-07-04
i've never been a huge fan of the restricted drivers manager myself.

try Envy instead [www.albertomilone.com](www.albertomilone.com)

---

### Post by psyopper on 2007-07-07
Wow, I found this thread while looking for more information on Enlightenment...

:)

Actually, [COLOR="Red"]**don't use Envy!**[/COLOR]

Your system is fine. If you are seeing some black windows this is a bug with the nVidia drivers that exists in all versions. The problem is memory management on the video card. The resolution is to add --indirect-rendering  to your compiz launcher.

It should look something like
```

compiz --replace --indirect-rendering

```

Do a forum search for indirect-rendering to learn more...

You will need to stop Compiz before starting any OpenGL based games. Compiz doesn't give up it's OpenGL hooks and forces your computer to attempt to keep rendering the desktop behind your fullscreen OpenGL game. Maybe on a Quad-core with dual 756 meg 8800GTS' it would work...

---

