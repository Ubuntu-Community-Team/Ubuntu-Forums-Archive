---
title: "Eduke32 and Playstation 3(R) Controller"
date: 2011-03-06
forum: Gaming &amp; Leisure
---

### Post by Viper1987 on 2011-03-06
Sorry for the length of this thread, but I usually google things for DAYS before I decide to post... it's been weeks...

Here's the problem: in Eduke32, everything works beautifully... i got all the add-ons and packs working after little troubleshooting... only thing: i'm using PS3's DS3 and i can't strafe or turn. Axes are as follows: axis0: left joystick's x-axis, axis1: left joystick's y-axis, axis2: right joystick's x-axis, axis3: right joystick's y-axis... axes 1 and 3 aren't working, which means no analog strafing or turning in-game. Whenever the joystick's enabled, i am unable to strafe or turn with the mouse either (even when i have all of the input devices for the game enabled)

Here's what i've tried:
Obviously, the first thing i did was install the joystick driver...

-Joy2Key- Doesn't emulate mouse
-qjoypad- mapped the mouse to the right joystick no matter in which direction i use the axes, it always walks backwards and turns simultaneously.
-xserver-xor-input-joystick driver - I edited the .conf file to map the mouse to the right joystick and THAT DIDN'T EVEN WORK. 
-export SDL_INPUT_JOYSTICK=/dev/input/js0... also export SDL_INPUT_JOYSTICK=/dev/input/event8 (event8 is my joystick)
:confused:

My (HOPEFULLY) temporary fix: use qjoypad and map the first axis to A & D for strafing and <- & -> for turning... i, however want more accuracy, because when i just tap either of those directions, it is far too sensitive..

PLEASE, SOMEBODY, PLEASE prevent me from dying before it's my time and HELP!!! :)

---

### Post by Viper1987 on 2011-03-07
Bump... :(

---

### Post by Viper1987 on 2011-03-07
In Mupen64plus, when i tried to use the gui to edit the control setup, it didn't work. It always said axis 12 was being used with every button i pushed... i had to edit the config file and got it working...

Supertuxkart: same thing... I didn't edit the supertuxkart file, but i always turn left when trying to drive... 

jstest shows everything's responding just fine...  the axes, in particular....


anyone? anyone? beuler? beuler?

---

### Post by TerminX on 2011-03-09
Unfortunately, I think our joystick code is still pretty crappy, especially on Linux.  I do have a Dual Shock 3 controller and a couple of Wii classic controllers, so joystick support will definitely improve eventually, but it probably won't be any time soon.  Sorry!

Patches are welcome. ;)

---

