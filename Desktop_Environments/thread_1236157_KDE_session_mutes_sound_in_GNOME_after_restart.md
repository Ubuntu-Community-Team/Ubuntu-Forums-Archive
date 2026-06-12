---
title: "KDE session mutes sound in GNOME after restart"
date: 2009-08-10
forum: Desktop Environments
---

### Post by qyot27 on 2009-08-10
This is a really strange issue I've been having lately.  I'm running an original GNOME-based install of 9.04, of which I additionally installed KDE so I could choose which environment to use at login.  4.2 really has me impressed.

At first, I was having issues because sound was fine in GNOME, but the only sound I could get in KDE was at login.  None of my audio apps would work, not even ones that installed with KDE itself, like Juk.  This was fixed by installing some additional plugins.  Now sound in KDE works fine, without question.

But I noticed something odd in GNOME.  Honestly, I'm not sure if this started happening before or after I fixed the sound issues in KDE, but it's fairly predictable.

I have GNOME set as my default DE (with autologin enabled, as no one else uses this computer), and therefore have to log out and log into to KDE later.  If I decide to restart or shut down the computer from KDE, then the next time I'm in GNOME, the sound is muted and at 0%.  ***However***, if I log out of KDE and log back into GNOME, the sound is fine - it isn't muted, and it's still at 80%.  Additionally, if I then restart or shut down from GNOME at this point, then audio is still fine the next time.

In short,
A. Autologin to GNOME.
B. Log out, log in to KDE.
C. Restart/shut down computer.
D. GNOME's audio is muted and at 0%.

but it's fine if,

A. Autologin to GNOME.
B. Log out, log in to KDE.
C. Log out of KDE, log back in to GNOME.
D. Restart/shut down computer.
E. GNOME's audio is fine - not muted and at 80%.

---

### Post by monkeyKata on 2009-09-10
Hello.

First off, I'm using KDE 4.3 from the ppa.  I had a similar problem as you, with both gnome and kde installed, which put my volume in gnome after coming from a kde session at just above mute and barely audible.  Right clicking the volume icon and going into Volume Control I found that the master was up but the PCM had been lowered to just above 0%.

Do you have Kmixer installed?  Under KDE, installing that was the only way I found to put a volume control icon in my notification area.  Right-click the icon and go to 'Select Master Channel...' and set it from PCM to Master.  This worked for me as the next time I logged into gnome the PCM volume was up as normal.  

Maybe that will do it.  And if you do read this and haven't forgotten this post, do you mind explaining which packages or plugins you installed to get sound working?  I haven't gotten music or video to play in KDE, though in gnome I have it set up fine.

---

### Post by qyot27 on 2009-09-11
The packages I installed to fix KDE's sound issue were:

libxine1-ffmpeg (1.1.16.3-0ubuntu1)
phonon-backend-xine (4:4.3.1-0ubuntu3) - I think this was the only one really necessary, but I installed both anyway.

I also installed these, but I'm not sure how much they were needed (if at all):
alsa-oss (1.0.17-1)
alsamixergui (0.9.0rc2-1-9)
libfltk1.1 (1.1.9-6)
oss-compat (0.0.4+nmu2)

---

