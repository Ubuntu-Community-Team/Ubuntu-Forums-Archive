---
title: "Gnome desktop won't start"
date: 2011-01-29
forum: Desktop Environments
---

### Post by caribedude on 2011-01-29
Hi, I've recently updated to Ubuntu 10.10. At first I had no problems, but after the third time I logged in, my desktop background appeared (and nothing else) but quickly flashed to a black screen with some error messages (too fast for me to see) and I got sent to the login screen. After trying some more times I got the same problem with some small differences(sometimes my desktop icons showed up, other times it took a couple of minutes before I got kicked out). I tried running startx from the terminal but got one of these two error messages: Server already running or could not find any listening ports. If I run "sudo startx -- :1" to switch the port I login fine, but as the root user. Gnome works perfectly here and when I login in gnome-failsafe. This leads to believe it has something to do with my user configuration. I've restarted xorg server, installed gnome-main-menu and made sure if got the current gnome package. I have no idea as to what to do and other forums have yielded no results, any help at all is appreciated.

---

### Post by hictio on 2011-01-29
Have you tried under a different (non sudo) user? For instance, the guest user?

---

