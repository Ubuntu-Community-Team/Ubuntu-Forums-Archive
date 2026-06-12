---
title: "mapping keys"
date: 2007-09-27
forum: Gaming &amp; Leisure
---

### Post by muski on 2007-09-27
hi .. i am new to linux and i wanted to remap a few keys on m keyboard for  dota/(warcraft)

F1 to space 
numpad7 to z
numpad 8 to x
numpad 4 to c
numpad 5 to v 

capslock (or any other key)  to become a toggle to enable alt key permanent on off .. ie
press caps once .. alt key is now permanent on
press again .. alt key is now off ... 

can anyone tell me how to create a script or any software (like autohotkeys for windows) in which i can do this.

i tried creating .xmodmap file but i am not able to create the alt key toggle in that (i dont know how to)

can anyone help ..
thanks a lot

---

### Post by ddrichardson on 2007-09-27
Use xbindkeys (man xbindkeys in the terminal will give you more information) and as for capturing key codes, run xev in a terminal and then when you hit the key you need the keycode is displayed.

---

### Post by muski on 2007-09-27
how do i create the action 

press caps ... alt on
press again ... alt off ...

this seems to be the biggest problem

---

