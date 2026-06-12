---
title: "beryl feisty and ati problem"
date: 2007-04-19
forum: Desktop Environments
---

### Post by Butcher_swe on 2007-04-19
i get the WSOD when i try beryl, and even when i try Desktop Effects and it runs whery whery slow... are there any howto's to install ati drivers for feisty? i get this when i runs glxinfo | grep render : direct rendering: Yes
OpenGL renderer string: Mesa DRI R300 20060815 x86/MMX/SSE2 TCL
I cant uderstand why Mesa doing there
/Butcher

---

### Post by beerorkid on 2007-04-19
I have a pretty lame ATI card here at work and just ran [this script]("http://forum.beryl-project.org/viewtopic.php?f=36&t=4781") which got me most of the way.  Feisty.

I did have to "sudo apt-get install beryl-manager emerald emerald-themes" afterwards though.  But I have used that script on another intel graphics PC and had no issues what so ever.

I am used to doing it the nvidia way so both above I just wanted to go the easy route.

as far as the ATI drivers [envy]("http://albertomilone.com/nvidia_scripts1.html") rules.  I find it works better when not in X though.

---

