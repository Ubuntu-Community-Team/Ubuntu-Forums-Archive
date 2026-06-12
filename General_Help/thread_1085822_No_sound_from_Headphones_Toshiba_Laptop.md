---
title: "No sound from Headphones Toshiba Laptop"
date: 2009-03-03
forum: General Help
---

### Post by KangarooStyle on 2009-03-03
Here's the problem. When I insert my headphones into the jack, I don't get any sound from headphones, and my laptop speakers stay on. The headphones work just fine on Vista, so I know it's not a hardware issue. I've done a search throughout the forums, and been searching Google, but to no avail. Here's the specs that I have if it will help.

Toshiba A135 S4527 Laptop
Ubuntu 8.10 Intrepid
Soundcard: ALC861-VD

Here's what I've tried:
1. Checked the Volume the control making sure that headphones weren't muted.
2. Edited modprobe and added "Options snd-hda-intel position_fix=1 model=lenovo"

One thing that I noticed is that when I right click on volume control > preferences > and go to Playback: ALSA PCM on front, it only has control for "Master" and not headphones, while the Realtek mixer, has control for headphones, but it does not do anything when it's selected.

Thanks for help!

Edit: Everything working now! Had to change "Options snd-hda-intel model=lenovo" and make sure PCM, and Front under the HDA Intel Alsa Device were all the way up!

---

