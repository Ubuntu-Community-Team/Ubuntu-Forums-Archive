---
title: "java crashing firefox"
date: 2005-10-31
forum: Desktop Environments
---

### Post by ubnoobie on 2005-10-31
the way the system was set up may come in to play, so i'll outline that first. problem and question follow....

have a pretty empty xfce4-based system i'm setting up on a friend's really old (k6/2, 160mb ram, 4gb hd, 8mb ati rage onboard) system.  base system only  install off of the (gn)ubuntu cd (followed by the 2 updates)... then:

adding packages (via aptitude) in this order.. including all 'recommends' except where noted.
xfce4, xfce4-terminal, xwindow-system-core, menu

*i don't particularily care for the package selection in xubuntu-desktop, which is why i didn't just use that...*

reboot (had forgot if xdm came with the core or not, was just checking while i fixed some grub; er... lunch), then:
nautilus (w/o recommends).. because xffm well. um.. sucks penguin doodoo.

*stupid me, i forgot about adding --no-desktop to nautilus menu entry so i lost xfce4's right click menu when i fired it up to make sure it was working*

then adding:
firefox, msttcorefonts

*so far so good..*

then adding:
flashplugin-nonfree, j2re1.4 (blackdown).

*and the world comes to an end.. during 'setting up j2re1.4', xfce4's bottom panel disappears (thus the significance of running nautilus w/o the extra switch). end up doing a sudo reboot after aptitide is finished and i was back to console.*

get back to the desktop to test firefox... flash is working (a little on the slooooow side due to the system being ancient to begin with), was testing it on macromedia's site. but go switch over to one of the java games at yahoo and firefox just up and diappears.. buh, bye. go in again.. buy bye...

try dpkg-reconfigure j2re1.4 -- this time choosing NO to the halt question (default is yes).  go back to firefox and it waves g'bye again.

i go over to [www.java.com](www.java.com), the main page's applet loads ok, but go to 'verify installation' and firefox vanishes again, just like at yahoo.

some other thread mentioned a possible font issue, so i tried disabling use document fonts like it suggested.. no dice.  (have since changed that setting back)

firefox and blackdown java are on my main desktop with a standard (gn)ubuntu install (and then some), and firefox does not crash on java pages with that system.

so, i guess the question is: what is this xfce4 system missing for java?

---

