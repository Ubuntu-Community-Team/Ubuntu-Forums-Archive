---
title: "m64py controller configuration issues"
date: 2013-07-03
forum: Emulators
---

### Post by SirGuineaPig on 2013-07-03
I recently installed mupen64plus 1.99.5 and m64py as the frontend. All the plugins work, everything works fine except for the controller configuration. It absolutely refuses to save any changes I make to the default controls and insists I use the defaults. Is there any way I could save the changes I make to it? I am using Xubuntu 13.04.

---

### Post by BigSilly on 2013-07-14
Bit late replying to this one, so hopefully you haven't disappeared in frustration! I know what this is like because I've had the same issue myself. I've only recently figured out how to fix it.

Basically the emulator is looking for a compatible joypad configuration with its config .ini (on Ubuntu 13.04 it's in /usr/share/games/mupen64plus/InputAutoCfg.ini). If there isn't a compatible preset, then you get stuck with the default keyboard settings and no way to change them. What I did was follow [this guide]("https://code.google.com/p/mupen64plus/wiki/ControllerSetup") to create a working joypad config to go in the .ini. The guide says you should be able to figure out your axis settings easily, but being a bit of a dumbo I didn't stand a chance at this off the top of my head as I don't have a working knowledge of axis settings on gamepads. However, this is where M64Py really helped me.

I opened the M64Py front end but via the command line using the m64py command. As you do this you will see in the terminal output the title of your controller in quotation marks. Mine is listed as 'Jess Technology Co., Ltd. USB Game Controllers', which does not feature in the InputAutoCfg.ini I mentioned before. So, I had to manually add it.

I then went into the M64Py GUI joypad settings and began configuring my controller. Here you can clearly see the output you need to accurately configure your pad and successfully edit the InputAutoCfg.ini. So you'll need to sudo gedit /usr/share/games/mupen64plus/InputAutoCfg.ini with the joypad settings GUI open, check the syntax used against settings that are already in the file so you don't mess up your config, and stick your data in. After this you should have a working, and editable, joypad configuration. Be sure and send the file to the dev. ;)

Hope this helps. Let me know if not.

---

