---
title: "Play Quake 3 Arena and listen to Music (Xmms)?"
date: 2005-06-24
forum: Gaming &amp; Leisure
---

### Post by snitride on 2005-06-24
](*,) Linux Noob needs help! 

first question...
I have an abit An7 mainboard with onbord sound. Alsa, Oss and esd are set up and running, also i have followed the Ubuntu guide allowing multiple usage by more then one app. But quake 3 hangs until i switch off esd or xmms player. 

second question...
Everytime i start Quake 3 and join a game my mouse disappears and the only way i can get it back is changing one of the quake 3 display settings, then my mouse works perfectly again :-? 

](*,)  Please help me

---

### Post by snitride on 2005-06-24
Here the solution

1. install artsd 

2. Start Artsd in console with "artsd"

3. Set up Xmms player to run on artsd 
-->Options -->Preferences -->Output Plugin --> select artsd 

4. start quake 3 with "artsdsp -m quake3" 

pronto ;)

---

