---
title: "SOLVED! 8.10 Guest Session Customization"
date: 2009-09-26
forum: Desktop Environments
---

### Post by fisherm on 2009-09-26
Maybe everyone else figured it out too, but it took me a while to do this and I found very little help online.

I wanted to customize my "Guest" session's default appearance (i.e. icon theme, wallpaper, and color scheme), and I got tired of customizing it every time it was used only to have those changes wiped out when "Guest" logged off.

I found my solution by editing the guest session setup script

/usr/share/gdm/guest-session/guest-session-setup.sh

I then simply added (or modified) the settings found in the section that was commented as "disable screensaver to avoid locking guest out of itself"

All this does is manually set the default gconf settings normally found in the "Configuration Editor" 

I put the wallpaper I wanted to use in a folder in my /usr/share/gdm/guest-session directory and added the icons I wanted to use to my /usr/share/icons directory.

I hope this helps anybody who was wanting to accomplish the same thing. Feel free to let me know if there is a more accepted or correct way to do this, or contact me if I need to explain more in depth.

---

