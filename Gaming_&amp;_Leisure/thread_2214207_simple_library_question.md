---
title: "simple library question"
date: 2014-03-31
forum: Gaming &amp; Leisure
---

### Post by hunx on 2014-03-31
i want to compile a library.so like joy2key to send joystick button presses as keyboard keys for load with LD_PRELOAD with my game

my idea is something like this

switch(joy.button)
{
   case "button_1" : key.s=true;   
}

i don't know where i start writting my library or what dependence i need, thanks in advance

---

### Post by efflandt on 2014-04-02
Instead of trying to write a library (which I would not know how to do either), does the game have something to configure the keyboard and have you checked if the joystick button registers in place of the keyboard key you want to substitute it for?

When I was running a steam game (under development) there was only one thing that did not work properly on my Logitech gamepad (the Dpad). The game had a gui for keyboard config, but not for gamepad config, although, it did have a gamepad.config file. So basically in the keyboard gui config for certain keys I did not use, I pressed Dpad directions instead, and those registered. Then I copied the result of those Dpad presses in the keyboard.config file to the proper parts of the gamepad.config file and the Dpad worked like it was supposed to when using the gamepad.

---

