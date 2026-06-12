---
title: "Overlayed background"
date: 2008-10-08
forum: Desktop Environments
---

### Post by Effigiem on 2008-10-08
Few hours ago, after one reboot, I faced the strange problem in gnome. The desktop (by which I mean the wallpaper and icons placed on it, I exclude all control panels) seems to be overlayed by solid black coloured plane. 
Neither clicking on the place where icons were works, nor it is possible to see the wallpaper. After trying to change the wallpaper nothing changes. 
The unusual phenomenum happens just milliseconds after pressing ctrl+alt+backspace shortcut that shuts down the X server. The overlaying plane disappears, and one is able to see the desktop for ~0.5s.
I tried rebooting, but the only thing that was changed by that is a color of a plane (it got the default ubuntu one), and sometimes it covers the whole screen.
It's worth mentioning that yesterday I made a system update, so the whole problem may be connected with the ATI/AMD display drivers (I use fglrx). I managed to make everything look fine after applying dpkg-reconfigure on xorg.conf, but the bottom line of that solution is no direct rendering.

I hope that the solution is simple and wait for your ideas.



PS.There's my xorg.conf attached to the post.

---

### Post by JNA on 2008-10-09
Are you using Compiz?  If so you might try shutting that down and see if that fixes it.  I had this same exact problem, but hitting ctrl+alt+backspace solved it for me.

---

### Post by Effigiem on 2008-10-09
Finally the problem seems to be fixed in the same way it started. After some restarts the compiz was shut down automatically and everything started to work. I ran it once more but without the "widget layer" plugin and everything worked fine, so the problem seem to be there.

---

