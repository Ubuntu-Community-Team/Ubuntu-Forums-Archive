---
title: "script to auto-start new unity session?"
date: 2012-10-12
forum: Desktop Environments
---

### Post by lukejaeger on 2012-10-12
I'm building a library kiosk for a school using a basically stock Ubuntu Desktop 12.04 installation. Desktop environment is Unity/LightDM.

There is a user 'kiosk' with limited rights and autologin enabled. At logout, /home/kiosk is wiped and replaced with a clean version. This is done via a script called by session-cleanup-script in /etc/lightdm/lightdm.conf and it works fine.

Here's what I can't figure out how to do: when kiosk logs out, after resetting the home directory back to its clean state, I'd like the computer to log kiosk back in to a new session. This isn't a function of autologin, because that only runs at system boot. 

I don't see anything in the lightdm.conf options that would enable this functionality. 

Ideally, the last line of my session-cleanup-script (which runs as root) should start a new Unity session for kiosk. Anyone know how this can be done?

---

