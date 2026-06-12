---
title: "Notification sounds not working"
date: 2009-01-21
forum: Desktop Environments
---

### Post by jimbog on 2009-01-21
I've been using Kubuntu for 6 months now, with only a few minor annoyances... Since upgrading to Intrepid none of my notification sounds are working, **except** for the logout tune when I shutdown.

However, in system settings -> notifications I can successfully test all the sounds. Nothing is muted in alsamixer or anywhere else, and audio works fine with Amarok, Firefox and VLC.

Any ideas? J

---

### Post by oaqster on 2009-01-21
had kindof the same issue on Hardy, the solution that worked for me was to use ALSA for all devides instead of Autodetect under System -> Preferences -> Sound -> Devices

hope this helps
- oaqster

---

### Post by jimbog on 2009-01-21
Thanks for the reply, but I don't seem to have that option in my sound menu. If I go to system settings -> sound, I can choose the output device for the notifications, but the choice is only between my soundcard (Intel 82801DB-ICH4) and Esound (which doesn't work).

---

### Post by jimbog on 2009-01-22
Has anyone got any further thoughts on this? I know it's not a serious problem, but I'd like to fix it.

---

### Post by hansdown on 2009-01-22
Hi jimbog.

Choose KDE Menu ->General tab ->Notifications ->System Notifications ->Player Settings tab.

You should be able to fix audio settings here.

---

