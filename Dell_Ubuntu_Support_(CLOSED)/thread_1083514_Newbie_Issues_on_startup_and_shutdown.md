---
title: "Newbie Issues on startup and shutdown"
date: 2009-03-01
forum: Dell Ubuntu Support (CLOSED)
---

### Post by luap2011 on 2009-03-01
hey, just got my dell mini 9 yesterday with ubuntu(first time dealing with it ever) and somehow i have managed to screw something up. on startup it says setting time clock everytime followed by fwh failure. everything on the shutdown screen goes by too fast for me to know what it says. i tried included my syslog file but not too sure what to put in here since its so long. and i know this isnt much to work with but if anything is needed just let me know.thanks in advance.

---

### Post by sirebral on 2009-03-01
What BIOS are you running?

Have you tried updating the software?

You say you managed to screw something up?  Retrace the steps you took to get to where you are.  Did you install something?  Did you change a configuration?

---

### Post by Rallg on 2009-03-01
I assume that the computer came directly from Dell, out of the box with Ubuntu pre-installed? If that is the case, there is the possibility that the unit is damaged. Dell does test units before shipment, though.

Do you have any peripherals attached? Anything at all: external mouse, memory card, USB, whatever. If so, unplug them and try again.

I know that the units shipping with XP have a Dell diagnostic partition. probably so do the Ubuntu units. If so, try this: Turn the computer on, and as the Dell logo screen appears, press the 0 (zero) key. You might have to do that more than once. This will bring you to a boot menu. Does the menu offer a diagnostic choice? If so, try it and see what happens.

Do you ever get to an Ubuntu login screen (where you enter a user name, or perform setup)? If you do, look in the lower left of the screen for Options. Try Gnome fail-safe. In your case, that might not make a difference, but if it does work, it indicates a driver problem. If Gnome fail-safe does not work, try Recovery (Terminal) mode. As the computer boots, you will see a lot of text on screen (no graphics). A few lines will indicate failure, but that might mean the system is looking for hardware that you don't have. But some failures could be important, particularly ones that appear towards the end, before you get to the prompt. What do those say?

If even the Recovery (Terminal) mode does not work, then you have a real problem, and it's time to contact Dell. If they tell you that you need to update the BIOS, that can be done outside of Ubuntu.

---

### Post by luap2011 on 2009-03-01
hey guys i appreciate your suggestions, but dell is going to send me a replacement refurbished dell mini 9 due to an obscene amount of scratchs and the bezel around the screen being popped out of place when i opened it out of the box. the dell ubuntu runs fine as of right now with no problems, so ill just wait for the replacement one to get here :)

---

