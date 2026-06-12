---
title: "Volume hidden under clock in unity panel!! Ubuntu 11.10"
date: 2011-10-18
forum: Desktop Environments
---

### Post by Truckerpunk on 2011-10-18
This is driving me mad... My volume indicator in the top right is hidden underneath the clock, after my upgrade to 11.10. I've tried to reset unity, restart unity, old guides to reset panels (I was desperate*), and NOTHING works. Why did the remove the option to move the icons in the panel as you please... oh why? And the alt+right click doesn't work either. Can anyone tell me how to move icons in the unity panel, or try to reset it to default.. something.. I need help, any help.

---

### Post by Truckerpunk on 2011-10-20
Found a solution!!

Here's what I did to get Ubuntu to recognize my soundcard, and display volume controls correctly in the panel:

sudo apt-get remove --purge alsa-base
sudo apt-get remove --purge pulseaudio
sudo apt-get clean && sudo apt-get autoremove
sudo apt-get install alsa-base 
sudo apt-get install pulseaudio

then restart your machine, your sound should be OK now.

---

