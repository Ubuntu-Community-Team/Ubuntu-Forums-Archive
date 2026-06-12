---
title: "N64 Emulator From Snap Store"
date: 2019-08-26
forum: Gaming &amp; Leisure
---

### Post by bionic3epl on 2019-08-26
Is there a possibility of setting up a Keyboard Control for the N64 Emulator from the Snap Store?

---

### Post by deadflowr on 2019-08-26
What's the emulator?

---

### Post by bionic3epl on 2019-08-26
I think it's called Mupen64+

---

### Post by deadflowr on 2019-08-26
I didn't think there was a snap version, but you should be able to set the keyboard as the joystick in the mupen64plus.cfg file.
In the normal apt version it's in  ~/.config/mupen64plus/ directory.

If it is snap then that path would be somewhere in the ~/snap directory.

But basically the config is set in the [Input-SDL-Control] section.
I thinkthe default is -1 for keyboard and 0 or more for joystick so set it to -1.

From there if you need to setup keybinding you can follow the sdl-centric keybinding found here:
[http://www.libsdl.org/release/SDL-1.2.15/include/SDL_keysym.h]("http://www.libsdl.org/release/SDL-1.2.15/include/SDL_keysym.h")

More on mupen64plus documentation here:
[https://mupen64plus.org/docs/]("https://mupen64plus.org/docs/")

---

### Post by bionic3epl on 2019-08-27
When I looked @ it, the whole config wasn't there, just the few short sections. Can you find a copy of the whole config file so I can replace it please?

---

### Post by deadflowr on 2019-08-27
What does it look like at this point?

---

