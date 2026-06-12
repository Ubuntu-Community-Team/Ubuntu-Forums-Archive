---
title: "Intel 855 GME &amp; KDE 4 driver issues"
date: 2008-11-06
forum: Desktop Environments
---

### Post by prox2far on 2008-11-06
I'm running an old laptop with a new install of Kubuntu 8.10. I have turned all effects of and tried with multiple video players.

Every time i start a video clip the player just displays a blue imgage, or KDE crashes and takes the system down as well after a few seconds of playback ie. forces me to do a hard reboot.

I have tried reconfiguring xorg and specifying intel, i810 and VESA as driver in xorg.conf. The i810 and VESA drivers gave a garbled image making it impossible to login, and the other attempts just gave the same error as above.

I have tried using IceWM and watching a clip from this WM and I have not experienced any problems here.

Anybody got any tips for what is the cause of this behavior or how to solve it?

---

### Post by arnasd on 2008-11-06
i have the same problem. have you solved it?
tried editing xorg.conf, but i could not solve it yet.

---

### Post by krazyd on 2008-11-06
what player are you using?

---

### Post by arnasd on 2008-11-07
personally I use VLC. tried to change its video output, but no luck.

---

### Post by prox2far on 2008-11-12
Sorry for the late reply, I have been under the impression that ubuntuforums didn't work, since I could not log in with Firefox.

I does not depend on the player, I have tried with Kaffeine and VLC, both give the same result. When I try to play a movie in IceVM or XFCE I don't experience any problems.

I have tried fiddling more around with this problem and I have decided that I will submit a bug report and wait until the KDE devs kan fix it, or they give me a good answer to why it does not work :(

-------------------

Edit

It wasn't kaffeine but dragon player I have been using.

---

