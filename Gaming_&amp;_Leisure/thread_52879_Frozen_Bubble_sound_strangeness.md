---
title: "Frozen Bubble sound strangeness"
date: 2005-07-29
forum: Gaming &amp; Leisure
---

### Post by dangerjunkie2002 on 2005-07-29
Hi,

I just added the extra repos to my Hoary Hedgehog install. I'm running Gnome on a Centrino laptop. I installed Frozen Bubble 1.0.0-6 with apt-get. 

If I run Frozen Bubble from the command line it gives a warning that it can't open /dev/sequencer but the sound and music work fine. If I launch it from the Applications menu I get no sound or music and it's impossible to tick the sound box on the Bubble menu.

In order to fix a problem I had with Skype (which I don't have running right now) I previously followed the instructions found on [https://wiki.ubuntu.com/SoundProblemsHoary?highlight=%28sound%29](https://wiki.ubuntu.com/SoundProblemsHoary?highlight=%28sound%29) and [http://alsa.opensrc.org/index.php?page=DmixPlugin](http://alsa.opensrc.org/index.php?page=DmixPlugin)

I would be grateful for any suggestions.

Thank you,
Paul.

---

### Post by dangerjunkie2002 on 2005-07-29
Hi,

Problem solved... I finally noticed the right FAQ section (I have Aspergers and reading huge documents is difficult) and this fixed it:

apt-get install libsdl1.2debian-all

Best regards,
Paul.

---

