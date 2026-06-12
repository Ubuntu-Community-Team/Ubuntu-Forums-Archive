---
title: "Microphone does not record"
date: 2009-04-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lindberg.bill on 2009-04-26
Latitude D510 Laptop
Ubuntu 9.04

Microphone does not work dispite clean install of 9.04 did not work on 8.10 either.  I have tried disabling pulse audio and correctly configuring alsa.  I wonder if there is a fix for this issue at all.  I have found no information indicating that this cannot be fixed only fixes that did not work for me.

---

### Post by Denny Johnson on 2009-04-27
Internal or external mic?
What is your "Digital Input Source" in Alsa?

---

### Post by kkkkdddd on 2009-04-27
For me it works on M1530, but you need to disable pulseaudio and set proper mic input.

In Jaunty:
1. /etc/pulse/client.conf : change "autospawn = yes" to "autospawn = no"
2. /usr/share/alsa/alse.conf : delete line with "/usr/share/alsa/pulse.conf"
3. disable it from running on boot:
-install sysv-rc-conf
-run sysv-rc-conf and delete all 'x' on the line with pulseaudio
4. Restart
5. "pgrep pulseaudio" should print nothing
6. Set Digital Input Source to "Digital Mic 1" in gnome volume configuration in options tab
7. Now it should work, but you should disable pulseaudio in Totem (I do not remember how).

---

### Post by tacantara on 2009-05-08
What's the secret to changing those system files?  I tried setting my privileges through System > Administration > Authorizations, but nothing took.  I'm an Ubuntu noob, so please keep it simple for me :oops:

---

