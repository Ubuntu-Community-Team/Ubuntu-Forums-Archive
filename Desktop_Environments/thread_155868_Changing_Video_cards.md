---
title: "Changing Video cards"
date: 2006-04-05
forum: Desktop Environments
---

### Post by Harrh on 2006-04-05
I have been using Ubuntu for about 3 weeks now.  I have decided to switch my  Ati 9700 pro out of this computer and put in a G4 ti 4600 but i have the Ati drivers installed currently.  What do i change in my Xconf? do i unistall the Ati drivers? i apoligize if somebody else has posted the same questions i have looked on this forum and couldnt find anything and i also googled.. any help is appreciated

---

### Post by dermotti on 2006-04-05
You could go into your xorg.conf, change your driver to "vesa". Uninstall ATI drivers. Uninstall ATI card. Install Nvidia card. Install Nvidia drivers. run **sudo dpkg-reconfigure xserver-xorg**

---

### Post by Harrh on 2006-04-05
[QUOTE=dermotti]You could go into your xorg.conf, change your driver to "vesa". Uninstall ATI drivers. Uninstall ATI card. Install Nvidia card. Install Nvidia drivers. run **sudo dpkg-reconfigure xserver-xorg**[/QUOTE]
Thanks for the reply il try that right now

---

### Post by dcstar on 2006-04-05
[QUOTE=dermotti]You could go into your xorg.conf, change your driver to "vesa". Uninstall ATI drivers. Uninstall ATI card. Install Nvidia card. Install Nvidia drivers. run **sudo dpkg-reconfigure xserver-xorg**[/QUOTE]
Good advice, but also with the Nvidia stuff you have to manually select "nvidia" rather than the default "nv" that dpkg-reconfigure goes to.

You can search for detailed nvidia driver threads in the forum if you have any trouble.

---

### Post by Zeroedout on 2006-04-06
[quote=Harrh]I have been using Ubuntu for about 3 weeks now. I have decided to switch my Ati 9700 pro out of this computer and put in a G4 ti 4600 but i have the Ati drivers installed currently. What do i change in my Xconf? do i unistall the Ati drivers? i apoligize if somebody else has posted the same questions i have looked on this forum and couldnt find anything and i also googled.. any help is appreciated[/quote]

Mind posting back if you get a noticible increase of performance in games? Currently, I am using a 9800, which I do not think is that much powerfull than the 9700, so let me know if the ti 4600 actually makes a huge difference.

---

### Post by Harrh on 2006-04-07
[QUOTE=Zeroedout]Mind posting back if you get a noticible increase of performance in games? Currently, I am using a 9800, which I do not think is that much powerfull than the 9700, so let me know if the ti 4600 actually makes a huge difference.[/QUOTE]
il post back a response when i test the ti 4600.  It seems that my other machine wont take my 9700 pro for some reason.  Oh well il just install ubuntu on it thanks everybody for the wonderful information and help

---

