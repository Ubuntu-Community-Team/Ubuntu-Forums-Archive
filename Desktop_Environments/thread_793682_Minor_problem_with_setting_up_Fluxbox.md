---
title: "Minor problem with setting up Fluxbox"
date: 2008-05-14
forum: Desktop Environments
---

### Post by christopher.were on 2008-05-14
I've recently install ubuntu 8.04 from the command line and loaded on fluxbox along with various programs such as firefox and pidgin and stuff like that. However I can't get the sound working. My best guess is that I need to install one of the packages from the ubuntu repos to let me do this, but I have no idea which ones. Of course this may not be the problem but I dont know what else it could be, all the videos and stuff play fine (youtube, vlc etc..)

Any help would be greatly appreciated
Chris

P.s. I'm not the most advaned of linux users FYI.

P.p.s. why is it in fluxbuntu took so long to get release when I installed fluxbox on ubuntu in a matter of minutes?

---

### Post by kerry_s on 2008-05-14
you probably need alsa->
sudo apt-get install alsa-base alsa-oss alsa-utils

then run> sudo alsaconf
reboot
then in terminal> alsamixer
arrow keys to move around "m" to mute/unmute(green is not muted)

---

