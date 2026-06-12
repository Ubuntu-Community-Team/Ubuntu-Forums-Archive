---
title: "Disable multiple sessions for single user"
date: 2012-12-10
forum: Desktop Environments
---

### Post by hadlock on 2012-12-10
I have a Win7 desktop (1920*1080), a Win7 laptop (1366*768) connecting via RDP (remote desktop) to an Ubuntu 12.04 desktop server running xrdp (linux Remote Desktop server).

On the desktop, I can login to the Ubuntu machine via remote desktop/xrdp, load up eclipse, virtualbox, chrome etc, logout, log back in and everything is still there how I left it.

When I go to login to the Ubuntu machine from my laptop, I get a fresh shiny new login with no apps running on the desktop. The other programs are still running in the background, but I can't access their GUI from this login. I'd like to be able to login to the same session the desktop had been using earlier, so I can pick up where I left off.

As I understand it, "mutliple concurrent sessions" is a feature... but I'd like that feature turned off. The Ubuntu machine is a file server that only one person logs in to directly. Most of my searches yeild how to turn off guest logins, but I can't figure out how to let me log in to the same session from both the desktop and the laptop. I suppose deluge has a daemon/web interface, but I've messed around with that before and it's a huge pain + I prefer working with remote desktop for things like virtualbox as well.

---

