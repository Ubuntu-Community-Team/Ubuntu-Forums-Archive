---
title: "problems with composite manager"
date: 2005-05-12
forum: Desktop Environments
---

### Post by tonysathre on 2005-05-12
at login i get a windows pop-up that says the composite manager crashed twice within a minute and has been disabled for this session...then another one pops up and says that to have shadows and translucency work i have to have xorg <6.8 and add an entry to the X config file...i dont rememeber ever trying to enable shadows and translucency so how can i make this go away

---

### Post by dave9191 on 2005-05-12
I have the exact same problem, but only since I tired to enable composite support in the control center. I havent had a chance to mess around more with it yet tho. 

Control Center > windows behaviour > Translucency 

get rid of the tick use shadows/transluency. That should make the error messages go away. 

And if anyone has been succesfull with proper transpacrency and cool eye candy then let me know :) Ill mess around with it more in a couple of weeks when i have more time. 

Dave

---

### Post by tonysathre on 2005-05-12
ya i just turned it off...im not even exactly sure what translucency does but i thought it would make my windows transparent which i wish i could do...is there any other ways to make windows transaprent

---

### Post by dave9191 on 2005-05-12
Yeh, that what its supposed to do, but its a work in progress and has to be set up properly with the composite manager being installed as well as the other stuff it compalins about. They arent set up by default. And it might not even work with some graphic card drivers. Ive yet to play around with it properly.

---

### Post by ensenadaubuntulover on 2005-05-27
[QUOTE=dave9191]I have the exact same problem, but only since I tired to enable composite support in the control center. I havent had a chance to mess around more with it yet tho. 

Control Center > windows behaviour > Translucency 

get rid of the tick use shadows/transluency. That should make the error messages go away. 

And if anyone has been succesfull with proper transpacrency and cool eye candy then let me know :) Ill mess around with it more in a couple of weeks when i have more time. 

Dave[/QUOTE]

**get rid of the tick use shadows/transluency. That should make the error messages go away. **


exactly  how do I ge rid of IT ? I been looking in desktop configuration and in control center and dont find how

---

### Post by dave9191 on 2005-05-27
click on the control center in the menu. Open the Desktop branch, window behaviour. Click on the Translucency tab and the tick box is right at the top. Check the screenshot if you want.

---

### Post by ensenadaubuntulover on 2005-05-27
thank you very much!!!  :) , The breaking glass sound was starting to annoy me at the begining of the session.

---

### Post by dave9191 on 2005-05-27
no probs man :) Its annoying me too, but im leaving it there as a reminder to try and get this stuff working one day when i have time. 


Dave

---

### Post by z-vet on 2005-05-28
To get composite to work you need to add a new section to your xorg.conf (don't remember an exact syntax: an error message saying it to you). I did it and got all the eye-candy working, but system became **very** slow and KDE was crashy. Another (and biggest) problem is, that you can't load NVidia's GLX module with composite enabled - i found it in Xorg.0.log - so if you want NVidia drivers working you have no choice...
I just wonder if it works better on newer cards: i have a GeForce 440 MX 128 Mb which is outdated a bit...

---

### Post by dave9191 on 2005-05-29
[QUOTE=z-vet]To get composite to work you need to add a new section to your xorg.conf (don't remember an exact syntax: an error message saying it to you). I did it and got all the eye-candy working, but system became **very** slow and KDE was crashy. Another (and biggest) problem is, that you can't load NVidia's GLX module with composite enabled - i found it in Xorg.0.log - so if you want NVidia drivers working you have no choice...
I just wonder if it works better on newer cards: i have a GeForce 440 MX 128 Mb which is outdated a bit...[/QUOTE]

Yeh, but first I need to work out how to get this working with an ATI card, and what Ive seen so far is not promissing.

---

### Post by z-vet on 2005-05-29
Sorry, man, i have nothing to say here... Wish you a good luck.

---

