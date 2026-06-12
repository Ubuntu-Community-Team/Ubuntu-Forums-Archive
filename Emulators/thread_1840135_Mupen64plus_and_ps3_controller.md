---
title: "Mupen64plus and ps3 controller"
date: 2011-09-07
forum: Emulators
---

### Post by codymyth on 2011-09-07
Hello everyone. I have downloaded Mupen64plus 1.99.4 off of their website and have ran their install script. I can run the game just fine and the keyboard controls work fine. I would like to use my ps3 controller for the controls though. All that I have read off the Internet says that nothing needs to be installed on ubuntu(or any linux) for the controller to work. The controller does not work with Mupen64plus though. It is supposed use the auto-config file to get the key mappings for the ps3 controller(yes, i made sure it existed) but it doesn't do that, it just starts the game with the keyboard as the controls. I have read the mupen64plus wiki for game controllers, but it shows the autoconfig not find a file and defaulting to keyboard, mine doesn't do anything. It doesn't even appear that it tried to find anything besides the keyboard.
 
Am I missing something simple? Is there like a 'switch' to make mupen64plus look for gamepads?

I downloaded sdljoytest from the mupen64plus website and when i run it with the controller plugged in it shows that the sony playstation controller is connected.

I can't get the ps3 controller to work with supertuxkart either, but I assume that gamepads aren't implemented for that yet.

Edit:
p.s. The controller was detected when i tried use mupen64plus 1.5 but only 2 buttons worked and i couldn't configure the controllers because it always read a axis movement before i could press a button. 
Thanks

---

### Post by codymyth on 2011-09-08
Does anybody know where to start or what things i can try?

---

### Post by frostwork on 2011-09-08
several hints which might help:

- using usb your sixaxis is detected as
"Sony PLAYSTATION(R)3 Controller"
  using bluez it is detected as
 "PLAYSTATION(R)3 Controller"
 (see dmesg).
make sure the correct on is in your mupen64plus InputAutoCfg.ini

- make sure /dev/input/js0 exists (press the PS button to enable the joypad)

- start the emulator via commandline and check if stdout prints problems

- remove/rename your old 
~/.config/mupen64plus/mupen64plus.cfg
maybe 1.5 config doesn't work with 1.99.4 (?)

good luck so far!

---

### Post by codymyth on 2011-09-08
I don't have a problem with the controller name because mupen64plus would show errors that it couldn't find the the right config controllers and then default back to keyboard (i think), but it doesn't even show its trying. joytest gave out the same controller name as the one in the autoinputconfig file. I use it plugged in via the USB right now, though i may buy a bluetooth dongle in the future if i can get all the emulators i want working. 

is a stdout a command a should run?

There is no visible errors when running mupen64plus (the 1.99 version is commandline only), it just acts like there isn't even a gamepad hooked up. It says: one controller found. one usable controller. keyboard/mouse.(not word for word) 

IT WORKS
I im not sure what i did, i just went through everything again and then ran the emulator again and it worked. thanks for all your help

Edit
Actually i think what made it work was deleting that config file from mupen64plus 1.5. Im curious why mupen64plus 1.99 was use a config file from a folder that 1.99 doesnt even make

---

