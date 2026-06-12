---
title: "why dont compiz effects work outside the ccsm windo??"
date: 2009-05-20
forum: Desktop Environments
---

### Post by icivilion on 2009-05-20
Hi all i had seached in the forum but didnt got exact what to do for my problem.... it may be silly one i am not able to figure it out...  i have installed compiz-fusion and it works fine only with that ccsm window mean to say all the settings will work only for the compiz fusion setting manager window ony . i mean to say that the compiz effects wont work for other folders when i open it or close it nothing happens like burn or glide.... where can i enable the settings for other folders???? and in system>preferences>apperance>visual effects nothing will be highlighted means none ,normal,exra this things ... if i select extra and check in ccsm whole thing would be reseted there..... can anybody help????? please:):confused:

---

### Post by gettinoriginal on 2009-05-20
Try going to System > Administration > Hardware Drivers, activate the driver, then go to Appearance > Visual Effects.  It will all depend on your graphics card, and you may have to search for a solution for that specific card.  If that does not work, then post again, and I we can try other things.  :p

---

### Post by icivilion on 2009-05-22
Hi thanks for the help when i open the hardware drivers it opened a dialoge  like this.. i didnt undrstood what to do.. any idea.. what hardware i shuld enable in it? please help i am totall dumb

---

### Post by gettinoriginal on 2009-05-22
Well, that shows that the driver is activated, so I am going to take you back to square one.  ;)  
First, open a terminal (Applications > Accessories > Terminal).  Copy and paste the following, it will reset compiz to default settings.
```
gconftool-2 --recursive-unset -a /apps/compiz
```
Now close the terminal, open CCSM, go to Effects, make sure that animations is checked.  Now click on the word animations, now you have the window to select which animation you want for each window behavior (tabs at the top).
Highlight the animation and either delete it or edit it to make your selection.   You may also want to install "simple-ccsm", it will install to System > Preferences > Simple CompizConfic Settings Manager. This is a much simpler GUI for changing behaviors/animations of compiz.  Don't worry about messing things up, as either the code I gave you above, or in CCSM, the little broom resets things to default.  :p

---

### Post by kiridude on 2009-05-22
Also make sure you have checked "animation add-ons"  - it is the icon next to "animations"

---

### Post by icivilion on 2009-05-24
friends... thanks for you time and help... my main problem is everythings works inside the compiz ccsm window.. even keeping that widow open and if i try for other folders or open any applications or folders the burn effect or any effects wont work for the other windows or applications.... and my desktop cube works fine and paint fire on screen and water effect work fine all time....... can you help... i think i am not able to explain the things properly here.... not too good in english... any one figure out...

---

### Post by icivilion on 2009-05-25
Thanks mates.... really thanks... the things started working automatically i dont know how... animations addons was getting disabled automatically eventhough i had saved it.. but now i dont know how its working...anyway thanks for help... now the thing is the desktop cube is not working eventhough its enabled!!!!! anyway i wil compromise with desktop cube....

---

### Post by kiridude on 2009-05-25
It depends on what you want to do with your cube. Make sure you have enabled the corresponding effects. For example, if you want to rotate your cube, you have to enable "rotate cube." Also check the key combinations to make your cube move in different ways under the "bindings" tab in "rotate cube." The best way is to fiddle around with the settings until you get it working how you want. Another good idea is to check out some of the vids on youtube that talk about the cube.

---

