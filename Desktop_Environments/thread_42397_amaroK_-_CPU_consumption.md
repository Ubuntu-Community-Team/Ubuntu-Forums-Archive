---
title: "amaroK - CPU consumption"
date: 2005-06-17
forum: Desktop Environments
---

### Post by @jens on 2005-06-17
Hello

KDE 3.4.1, amaroK 1.2.4, PIII 1Ghz, 256 megs SDRAM

After starting amaroK the CPU consumption raises to 100% after ~1,5 minutes, the system slows down, any other application like kmess/firefox  isn't usable anymore. 
It doesn't happen with similar heavy  players like kaffeine, xine or xmms. 

I couln't find the prob in amaroK's bug list. Anybody out there who experienced the prob? Any solution for that?

Thank's very much
@jens

---

### Post by beefsprocket on 2005-06-17
[http://lists.kde.org/?t=110986016200001&r=1&w=2](http://lists.kde.org/?t=110986016200001&r=1&w=2)

Suggests that there is a 100% cpu usage issue when minimized. Have you tried the 1.3 beta that is out now?

---

### Post by Freddy on 2005-06-17
Witch soundserver are you using? at amaroK's homepage they address your problem with high cpu usage at their faq, 
Try install Gstreamer (it's probaly in your repos) and use Gstreamer insteed.

/Freddan

Edit: Gstreamer is the sound engine the developers recommend and I got amaroK pretty stable using that.

---

### Post by @jens on 2005-06-18
Hello

I tried all available servers (gstreamer/xine/arts). Unfortunately the prob persists. I'll wait for the stable 1.3 and will try again. It seems that this prob only occurs on some (older PIII?) machines.   

Thank's for your reply!
Regards,
@jens

---

### Post by beefsprocket on 2005-06-18
Apart from a tricky install (dependencies) 1.3 seems quite stable to me. If you compiled it with the checkinstall utility you could also have an easily uninstalled .deb package customized for your system. Just a thought.

---

### Post by z-vet on 2005-06-18
@jens:
I use an 1.3-beta SVN which i update every day. No problems at all, so i think you don't need to wait for a release, just get the beta and install it.

---

