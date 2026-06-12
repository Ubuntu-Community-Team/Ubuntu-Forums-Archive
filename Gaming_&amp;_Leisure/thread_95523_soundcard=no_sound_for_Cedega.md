---
title: "soundcard=no sound for Cedega"
date: 2005-11-26
forum: Gaming &amp; Leisure
---

### Post by ToiletDuck on 2005-11-26
Just installed Cedega 5.0 and all is going great, game support (at least for me) is the best it's been. Till now i have been using the on-board sound but the constant in and out of white noise forced me to add a pci card. Now i cannot play with the OSS checked in the profiles for my games. If i check the ALSA tab the games run fine but with no sound. Just tried Steam DOD and while loading with OSS checked i get "sound device in use" when i cancel out i end up hard booting as the screen locks up. Im not sure as to what tests or screenshots i could show to you? Any support would help im sure. Specs below.

P4 2.1
80 gig HD
512 ram
Dynax pci soundcard
Cedega 5.0
Ubuntu 5.10 Breezy

Thanks,
TD

---

### Post by madjinx on 2005-11-27
try using ALSA, but open a terminal and tyep

killall esd

esd sound process often interferes with ALSA sound thread, and causes games to not have sound.

---

