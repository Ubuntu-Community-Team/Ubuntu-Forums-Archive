---
title: "How to configure controls for mednafen?"
date: 2007-11-28
forum: Emulators
---

### Post by Scooter7 on 2007-11-28
Hi, I've installed Mednafen (emulator), and it works great, but I can't figure out how to configure my gamepad to work with it.

When I run it (mednafen /path/to/rom), I get this:

> Starting Mednafen 0.8.1
 Loading settings from "/home/vertimyst/.mednafen/mednafen.cfg"...
 Initializing joysticks...
  Joystick 0 - Logitech Logitech Dual Action - Unique ID: ce96ea6b9d7ca56a

Once I'm in-game, I hit F1 for the help.   One of the options is 'F2 - Configure Command Key'.   So I hit that.

This is where it gets confusing.   At the bottom of the screen, I get 'Press a command key now'.   Here, I assume I'm supposed to go 'alt+shift+n' (where n is the port - I have no idea what number I'm supposed to use, though, so I tried 1).

I get random responses each time, from nothing at all to '1(1)', '1(2)', etc.   I think this is because I've messed up the configuration or something.   I'm doing a reinstall right now.

So does anyone know how to configure the controls in this program?   I've looked all over, and some people say to use F4 (a non-existent shortcut in my version), while others have said to simply do alt+shift+n right from the start, which also does nothing for me.

-EDIT-

Nevermind, I managed to figure it out.   It turns out that by configuring the 'command keys', I had messed up the emulator shortcuts.   Since reinstalling mednafen didn't fix this, I realized that the config file wasn't being recreated.   So I manually deleted it, and that fixed the problem.

So, to configure the controls, start Mednafen and load your rom:

```
mednafen /path/to/rom
```

And hold down alt+shift and press 1.   It should display a direction/button, followed by a number.   Simply press the key you want to use for that direction/button.   Pressing it a second time confirms the setting, and the setup moves on.

---

### Post by Stormspireiv on 2007-11-28
> **Scooter7 said:**
>  Pressing it a second time confirms the setting, and the setup moves on.

You can also use that to set multiple buttons to the same command. The program knows you are done when you press the same button twice.

---

### Post by zizzdude on 2008-06-24
any way I can configure a joystick or game pad to the game? in the command line, I can see my game pad ID/name.

---

### Post by Scooter7 on 2008-06-24
You should be able to do that using the method I described.

Just load your game with mednafen, then

> .. hold down alt+shift and press 1. It should display a direction/button, followed by a number. Simply press the key you want to use for that direction/button. Pressing it a second time confirms the setting, and the setup moves on.

---

### Post by Scooter7 on 2008-06-24
Edit: Oops, sorry for the double post, my wireless card died as I was posting.

---

### Post by zizzdude on 2008-06-24
weird, doesn't seem to work, only the keyboard works. :???:

---

### Post by Scooter7 on 2008-06-24
Hmm, when you start mednafen, does it list your gamepad, like it does for me (see my first post in this thread)?

Maybe try restarting your computer with it plugged in, if you've been plugging it in after starting your computer.   Also, make sure it's plugged in before starting mednafen, otherwise it won't detect it.

---

### Post by zizzdude on 2008-06-26
yes, course its a different game pad. :p

edit: even though I see my game pad in the console, I cannot use the buttons on it. is there some type of configuration I need to do for my laptop? I'm using dell inspiron 1501.

---

### Post by Adm.Wiggin on 2009-01-15
I found that I had to run through joystick calibration first.

Just run jscalibrator from the command line.

On Ubuntu, it's in package 'jscalibrator'.  Just remember to Save your calibration after you run through the steps.

Mednafen doesn't seem to recognize an Axis as a button, however.  Too bad, I was looking forward to using my GameCube controller with Mednafen and my GC->USB converter. (The buttons work, but not the Axis.)

---

### Post by Veerappan on 2009-01-31
I'm having the same problems with Mednafen as Adm.Wiggin.  I've managed to get Mednafen to recognize every button on my gamepad (USB->PS2 adapter) except for the X/Y Axis.  jscalibrator works fine, and I've been able to grab the raw input from /dev/input/js0 to verify that the input is being transmitted, but it seems that mednafen doesn't currently work correctly with the X/Y axis on gamepads.

I'll be attempting to grab/inspect the source in a bit.

---

### Post by Mednafen on 2009-02-03
Sure it does.
Some joystick calibration programs fubar the reported axes ranges, though.

---

### Post by TpyKv on 2009-08-08
Thanks very much to all the helpful people on this thread :)

---

### Post by Zelphir on 2013-02-13
> **Scooter7 said:**
>  -EDIT-

Nevermind, I managed to figure it out.   It turns out that by configuring the 'command keys', I had messed up the emulator shortcuts.   Since reinstalling mednafen didn't fix this, I realized that the config file wasn't being recreated.   So I manually deleted it, and that fixed the problem.

So, to configure the controls, start Mednafen and load your rom:

```
mednafen /path/to/rom
```And hold down alt+shift and press 1.   It should display a direction/button, followed by a number.   Simply press the key you want to use for that direction/button.   Pressing it a second time confirms the setting, and the setup moves on.

 Can you please rephrase this or explain in more detail? Alt+Shift+n doesn't do anything for me, neither when I pressed f2 nor before. F2 makes that line appearing at the bottom, which tells me to press the button which I want to reconfigure, but how am I supposed to know on which buttons which action is at that moment?! Can't figure it out, either it is too obvious or simply not working. I tried the num block, the arrow keys, f3, f4, wasd keys, nothing seems to be working. Also Alt+Shift+1 doesn't do anything, regardless if I pressed F2 before or not.  Can someone help me out? 

EDIT: Nevermind... I had to first press Alt+Shift+2 to make mednafen show me a message about the second controler and THEN I was allowed get a response from mednafen when pressing Alt+Shift+1. I don't have any idea why it wouldn't let me configure the inputs for the first controler in the first place, but now it finally worked as it should. Guess you simply have to mash buttons until you make it work by accident :D

---

### Post by Perfect Storm on 2013-02-13
Old thread. Closed.

---

