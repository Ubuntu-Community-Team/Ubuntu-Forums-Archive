---
title: "VLC fullscreen mode doesn't fit the screen ?"
date: 2006-06-23
forum: Desktop Environments
---

### Post by IbeeX on 2006-06-23
Hi

I have Ubuntu 6.06 amd64

and when I press full screen in VLC I dont get full screen in stead I get Maximized vindow?

Do andybody have any idea why?

:confused:

---

### Post by IbeeX on 2006-06-27
anybody?

---

### Post by art on 2006-06-27
I have the same issue, would be happy to hear some solution...

---

### Post by IbeeX on 2006-06-27
Hi

I opened bug for this in launchpad

[https://launchpad.net/distros/ubuntu/+source/vlc/+bug/51117](https://launchpad.net/distros/ubuntu/+source/vlc/+bug/51117)

so feel free to coment

:-k

---

### Post by chrisccoulson on 2006-07-05
Mine seems to fill the full screen, with no border and completely hiding the GNOME panel. To get it to work, I had to go Settings => Preferences => Video => Output modules => XVideo, then check 'Advanced Options' and check 'Alternate fullscreen method'. This works for me.

ibeeX - I notice in your bug report that you say this option didn't work. I noticed that the alternate full screen method tickbox also seems to appear under the X11 and OpenGL menus within VLC preferences. These didn't appear to have any effect on my system though. I had to check the option under 'XVideo'.

---

### Post by IbeeX on 2006-07-06
[QUOTE=chrisccoulson]Mine seems to fill the full screen, with no border and completely hiding the GNOME panel. To get it to work, I had to go Settings => Preferences => Video => Output modules => XVideo, then check 'Advanced Options' and check 'Alternate fullscreen method'. This works for me.

ibeeX - I notice in your bug report that you say this option didn't work. I noticed that the alternate full screen method tickbox also seems to appear under the X11 and OpenGL menus within VLC preferences. These didn't appear to have any effect on my system though. I had to check the option under 'XVideo'.[/QUOTE]

Hi I use XVideo and when I check alternate metode then first time I click full screen it works OK, but then when I go normal screen and again full screen next time gnome panell is on top off full screen?
:confused:

---

