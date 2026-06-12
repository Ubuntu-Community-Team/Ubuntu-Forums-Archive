---
title: "install experience on 7150 and 42'' plasma"
date: 2008-05-07
forum: Desktop Environments
---

### Post by at0mic on 2008-05-07
hi,

i know a fair amount of people have had trouble with the 7150 video chipset. First attempt at installing 8.10 was rough as it did not detect my screen resolution and was stuck with 640 res. After install the desktop was in the same low  res. I attempted to change to resolution but could not through common administration tools. Obviously the restricted nvidia driver had to be installed. I installed the driver which worked great for my regular small monitor to get into high res. My plasma however required more effort. I had to update the synaptic package manager then install nvidia-settings. Once i had nvidia settings i had to change the resolution to 1024x768 which was harder than it shoujld have been really. clicking a button like the settings of the particular plasma monitor would cause the screen to jump instead of activate the actual button . Same goes for trying to click all the other buttons. Very weird. I found better luck navigating with the tab and enter key. I also had to run nvidia settings with "gksudo nvidia-settings" then hit the save button for settings to stick on next reboot. Once in 1024x768 which is my plasma max im off to the races.

---

