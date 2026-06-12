---
title: "Ubuntu Lives On Dell E1505N"
date: 2007-06-12
forum: Dell  Ubuntu Support
---

### Post by fjgaude on 2007-06-12
I ordered my full-up 1505 on 6/31, got it today. Have upgraded the OS without incident. All works, sound, LAN, WiFi, video... and most of all, the 1680x1050 screen. I've never worked with such dot-pitch before. Must be better than .22mm... the normal screens run from about .255 to .285. Will have to calculate just what it is.

Dell has changed the drive layout from the first machines shipped during the first week, 6/24 or so. Still boots to (hd0,2) but upgrades don't automatically go to (hd0,0). Very quiet, no fan noise, temp is 58C. Warm, but it is a notebook computer.

My video is using "nv" driver and gets 610 FPS on glxgears. I believe with the "nvidia" driver I'll get something like 2000 FPS. Having too much fun now to install the high speed driver.

Overall, very pleased with Ubuntu Dell.

frank

---

### Post by bunted on 2007-06-12
My e1505n came from the very first batch.  I never had an nvidia option.  I am so jealous.

---

### Post by fjgaude on 2007-06-12
The advanced nvidia driver is available on Synatics. Do a Search for nvidia, and you will find it. Install. Then

  sudo nvidia-glx-config enable

I do believe others have it working correctly on their 1505s. I'll likely do it in a few days, after I have the laptop setup with all my files for traveling.

Good luck,

frank

---

### Post by camarojones on 2007-06-13
> **fjgaude said:**
> The advanced nvidia driver is available on Synatics. Do a Search for nvidia, and you will find it. Install. Then

  sudo nvidia-glx-config enable

I do believe others have it working correctly on their 1505s. I'll likely do it in a few days, after I have the laptop setup with all my files for traveling.

Good luck,

frank

Is this the Restricted driver, or a 3rd party version?

---

### Post by fjgaude on 2007-06-13
> **camarojones said:**
> Is this the Restricted driver, or a 3rd party version?

Well, for what I know, there are only two Nvidia drivers: one for which the community has the source code, i.e., nv; and, the one that is restricted, i.e., nvidia.

If you go to System/Administration/Restricted Drivers Manager the menu shows what you have.

The nvidia-glx driver is likely the same as nvidia. Maybe someone else here has a firm answer. Is not 3rd party and restricted the same?

frank

---

### Post by fjgaude on 2007-06-20
After changing out "nv" with "nvidia" the glxgears benchmark program went from 610fps to 1900fps. Now that's a difference! (My desktop box runs at 5500fps but it uses PCI-E nvidia 7600 GS. Laptop is PCI Go 7300. I'm a happy camper so far.)

I've not been able to reliably use hibernate or suspend. I used the etc/default/acpi-support file to tweek, but with no real success. Any suggestions.

frank

---

### Post by binkl on 2007-06-21
I have the same laptop (which I like very much). I don't have trouble with suspend and the nvidia drivers as long as I don't turn on Desktop Effects. I've tried hibernate also and that works too, but I don't use it nearly as often. One nice thing about suspend is that I can just open it up and ubuntu resumes very quickly.

binkl.

---

### Post by fjgaude on 2007-06-21
I don't disagree with what you say. The key word was "reliably". Suspend seems to work most of the time and then, on coming back I lose my LAN or something like that. Then have to reboot.

Hibernate doesn't ever come out. I have to reboot each time.

I would think that with the right tweek we could get full reliability out of them, suspend and hibernate. In time...

Any help, anyone?

---

### Post by w30 on 2007-07-19
On my E1505n the secret was to change the synaptic repository from US to main and then when I went to the System>preferences>desktop effects and entered enable 3d desktop the window instead of just closing with no error and no effect then took me to synaptic and downloaded the  proprietary nvidia drivers that my card needed and installed them. A notice told me to reboot and run the 3d desk chooser again with the drivers booted. Cool eh! After that you need to open System>preferences>GL desktop and enable that. My system came with the synaptic repository set to main restricted multiverse etc. All boxes checked.

---

