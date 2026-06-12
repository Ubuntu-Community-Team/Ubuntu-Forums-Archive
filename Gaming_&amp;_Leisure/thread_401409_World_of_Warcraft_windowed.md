---
title: "World of Warcraft windowed"
date: 2007-04-04
forum: Gaming &amp; Leisure
---

### Post by Murxidon on 2007-04-04
I'm just wondering..

I've installed and updated WoW in WINE, but is there any way I can play it in windowed mode?

Thanks.

---

### Post by Gorthus on 2007-04-04
Well, if you want the game itself in windowed mode, then you will hit ESC, Video Options, and check WINDOWED...

If you want a Wine Virtual Desktop, do the following:

Open a terminal
```

winecfg

```
Hit GRAPHICS tab
Check Enable Virtual Dektop
And enter 1024x768 or whatever floats your boat.

---

### Post by slverlight on 2007-04-04
I believe that the "Wine Virtual Desktop" method outlined above is best from a performance perspective, but I was annoyed by the inability to resize the window or maximize it to fit precisely into the desktop window. If you want to run it in a Window as outlined in the early part of the above post (suing WoW's built-in windowed mode), you won't be able to cick the "Windowed" tab if you're running in OpenGL mode (game will crash, well documented bug). However, you can enable this option manually by opening the "config.wtf" file located in the <WoW Root Directory>/WTF folder. Add the following:

```
SET gxWindow "1"
```

This will tell the game to run in windowed mode with the resolution you specify.

- s|ver|ight

---

### Post by Murxidon on 2007-04-04
Thanks alot guys, the config.wtf fix works like a charm.

But.. Heh.. A different problem, WoW uses "Alt" alot for keyboard shortcuts, but Ubuntu seems to dissalow this.. Displaying the grab cursor in place of the WoW one..?

Any way to fix this?

---

### Post by Gorthus on 2007-04-04
Go to System>Prefrences>Windows and change the bottom radio options to either control or super.

---

### Post by Murxidon on 2007-04-04
Ohh.. So simple, everything's alright now.

Thanks alot everyone.

Wait.. Erm.. One more question... Whenever I use the "kill" process after looking up the number with ps -ax |more, it doesn't seem to kill the process? It's just when WoW crashes, or I want to quit it, it doesn't seem to do it properly and I still get annoying sounds/slowdown.

---

### Post by Murxidon on 2007-04-05
> **Gorthus said:**
> Go to System>Prefrences>Windows and change the bottom radio options to either control or super.

After just installing Beryl, it resets and I cannot use the usual Windows box, as it says Beryl has not registered a configuration tool...?

Trust me to mess it all up..

Help :P

---

