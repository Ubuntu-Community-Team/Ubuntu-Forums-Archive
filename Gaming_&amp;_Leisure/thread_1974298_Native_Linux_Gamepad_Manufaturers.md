---
title: "Native Linux Gamepad Manufaturers"
date: 2012-05-05
forum: Gaming &amp; Leisure
---

### Post by Omegus on 2012-05-05
I am planning on buying the Wireless Gamepad F710 by Logitek and thought to my self. With the advent of EA and Valve showing interest in Linux, what about gamepads? Has say the team behind Open Pandora thought of making Linux specific gamepads? Would Logitek be willing to work with Canonical to fully make the Wireless Gamepad F710blazing fast on Ubuntu?

I play Trine and a few others on Desura and I have to use my 360 controller, which is fine but I like everything on my computer to be Microsoft free. What are your thoughts on a a native linux gamepad?

---

### Post by doorknob60 on 2012-05-06
What do you mean by Linux native gamepad? Every gamepad I own works natively in Linux, whether it's Logitech, Sony, Nintendo. Anything I can get plugged in to my computer, it seems to work fine.

---

### Post by Grumbel on 2012-05-07
There really is nothing Linux specific about gamepads. If a gamepad makes proper use of USB HID, then it will work on any OS, with no extra drives or anything, it's all Plug&Play.

The issue with why gamepads and joystick can be a little annoying in Linux has nothing to do with the gamepad itself, but with the lack of standardization in games. On Windows the current way to handle gamepads is via XInput[1] and XInput is essentially limited to just Xbox360 controllers. So a game can be designed specifically with the layout of a Xbox360 controller in mind and many games don't even allow button remapping for that reason. If you plug in a Xbox360 controller it will work exactly as designed.

On Linux in the other side there is no limit. A gamepad or joystick can have as many axis and buttons as it wants to. Its basically the same situation as on earlier versions of Windows with DirectInput. While this means more freedom for the hardware designers, it also means a game has no baseline to design for. A game can't depend on analog triggers, as a gamepad might not provide them. The layout of the face buttons might be different and so on. In the end it means the user has to manually configure his gamepad with each game and every game to get it working and even after that it might not work very well.

Sadly there is no easy fix for that. You can make the gamepad programable or you can build a driver that allows remapping (qtsixa, joy2key, xboxdrv, etc.), but that doesn't fix the situation, it just gives you a bit more freedom in hacking together workarounds.

The only real way I can think of fixing that situation would be to generate a huge database with all the gamepads and joysticks around and then map them to the Xbox360 layout and then throw that into SDL. But even with that done, you would still have to fix all the games so that say actually use that standard layout.

[1] Not to be confused with the unrelated Linux X11 input stuff by the same name

---

### Post by Omegus on 2012-05-07
Thanks, that was actually very useful information. I never knew there was so much into stuff into how they function. Thanks

---

