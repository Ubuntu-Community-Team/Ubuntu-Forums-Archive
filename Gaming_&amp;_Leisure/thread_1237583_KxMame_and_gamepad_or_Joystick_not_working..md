---
title: "KxMame and gamepad or Joystick not working."
date: 2009-08-11
forum: Gaming &amp; Leisure
---

### Post by Bjorg on 2009-08-11
I can't get my joystick to work with KxMame.

Even the **Joystick Calibration** app from Add/Remove... has detected properly my Logitech Dual Action and says the joystick device is: */dev/input/js0*

This program detects everything in the joystick, every button, the 2 analog sticks and the digital pad. 

Even the KxMame frontend can be controlled with any of the analog joysticks or the digital pad, and the games launched with the buttons.

But once the Mame emulator is launched I lose the gamepad.

I have read somewhere after googling for it, that it is good to set KxMame's control as Standard Joystick and leave the Joystick Device Prefix without the final number (this way if you someday connect two gamepad it will recognize both automatically). By default it is set on */dev/js*

Either on */dev/js* or */dev/js0* or as the **Joystick Calibration tool** says in */dev/input/js* or */dev/input/js0* I can't play a mame game with the Joystick.

I can fire and use bombs (1st and 2nd trigger in a vertical scroller) but none of the directions in any stick or pad in the gamepad.

Anyone has achieved playing KxMame with a gamepad?

--------------------------------------------------------------------

**I have also tried configuring it from inside Mame:**

I have tried to configure mame once the game is launched and configure from there the buttons. I hit TAB and enter the configuration menu, from there I have seen:

Up: Joy 1 axis 2 neg (which is the wrong axis)

But hitting enter and moving a Joystick I can't assign that direction to Mame. Does anyone know how to enter the correct Joystick # and axis #. As I can see them from the **Joystick Calibration** tool I could set it manually.> [QUOTE][/QUOTE]

---

### Post by 4nayo on 2009-08-16
hi, with this it will functions...but...I have the italian version, then i'll write in italian:) from the menu choose:
impostazioni-->configura kxmame
then choose the tab "varie"
tip the box "usa opzioni aggiuntive" and write in the textbox this:  *-joytype 5*

then your joystick will function:)

---

### Post by Bjorg on 2009-08-16
Thanks for the answer:

As I am from Spain I understand you say:

[I]hi, with this it will functions...but...I have the italian version, then i'll write in italian:) from the menu choose:
Settings-->configure kxmame
then choose the tab "Miscellaneous"
tip the box "use additional options" and write in the textbox this:  -joytype 5

then your joystick will function:)[/I]

I will try tomorrow since I haven't got the gamepad here today.

I will post the result soon. Thanks

---

### Post by 4nayo on 2009-08-17
this is a screenshot:
[IMG]http://img268.imageshack.us/img268/3636/joystickkxmame.png[/IMG]

---

### Post by disturbedite on 2009-08-17
you failed to mention whether you are using xmame or sdlmame.

xmame should not be used as it seriously outdated and no longer maintained.

use sdlmame if you are not.

for a frontend i'd recommend moving to QMC2 or Mame Executor.

---

### Post by Bjorg on 2009-08-18
It works amazingly well. I have tried with an XBox360 gamepad for windows, (for PC, with USB connectors). Ubuntu 9.04 detects it instantly.

I only had to add that "-joytype 5" option.

Thanks alot!! :D

---

### Post by Bjorg on 2009-08-18
My KxMame is the default installation by Ubuntu. So it uses sdl-mame. Works very well.

---

### Post by disturbedite on 2009-08-18
i noticed that you're using kde4 (like me) and QMC2 & Mame Executor are both written in Qt4 like kde4 unlike the severely outdated and no longer developed kxmame.

---

### Post by 4nayo on 2009-08-18
To Bjorg: I?ve just won a match with my girlfriend at puzzle bobble...:) I hope u have fun!!!;)

To disturbedite: The first frontend for mame I've found in adept is kxmame...then I use it...but...I'll try QMC2, thanks for the information :)

---

### Post by Bjorg on 2009-08-20
I am using KxMame because my policy is to only install oficial Ubuntu packages from the Add/Remove apps .... menu

But I will investigate about QMC2 and Mame Executor.

4nayo:The games I love are mainly vertical shooter scrollers, like the 1945 saga, everything Cave, Atlus, Psykio, and also shooter from konami and others. Also the fighters as King of fighthing, Art of fighthing, street fighter, etc ... in general terms, and many others very good ones.

---

