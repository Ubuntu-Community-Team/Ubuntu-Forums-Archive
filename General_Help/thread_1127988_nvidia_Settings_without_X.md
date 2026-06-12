---
title: "nvidia Settings without X"
date: 2009-04-17
forum: General Help
---

### Post by raphael() on 2009-04-17
Hi,

Just curious to know is there any way to control Nvidia Graphic card settings from the console without starting X? I boot into text console & then start X as needed.

My card is 9600GT & I've added commands

nvidia-settings -a 'GPUOverclockingState=1' \ 
-a 'GPU3DClockFreqs=175,225'

through a script to Gnome Autostart. OS is Intrepid 8.10 & drivers are official 180.44.

---

