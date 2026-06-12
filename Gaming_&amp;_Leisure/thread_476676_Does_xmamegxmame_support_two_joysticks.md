---
title: "Does xmame/gxmame support two joysticks?"
date: 2007-06-17
forum: Gaming &amp; Leisure
---

### Post by richardwad1 on 2007-06-17
I'm having trouble gettign it to support both gamepads. In the options, it only lets you specify one of them. Both of them work just fine as player one....I can't figure out how to get another one to work. I posted a thread earlier about joy2key, but I couldn't figure out how to get tht to work. I would rather go with staright joystick if I can.

---

### Post by leech on 2007-06-17
gxmame needs some serious love.  It hasn't been updated in years, and doesn't work with sdlmame.  Well I think someone hacked a quick patch for it somewhere, but anyhow, the joystick support has been broken too.

It SHOULD work though, I believe you may have to load up the game you want to play, then hit the tab key.  This will bring up options for setting your joysticks to player one and player two.

I think you can also set it up in Mame that way for all games, if I recall correctly there should be an option there (under the tab menu again) for "This game only" or "generic" or something like that.  Been awhile since I played with it.

Leech

---

### Post by richardwad1 on 2007-06-17
I know all that, but the tghing is, GXmame controls the hardware configuration part of xmame. It will only detect one joystick in it's config menu. It ask for a prefix like dev/input/js it sya s in the documentation to not put a number after js and it will automatically cycle through them all, but it always just defaults back to js0. I can type js1 and make the other joystick work though.

---

### Post by Kangaroo on 2007-09-07
I remember, that in past versions of gxmame it was possible to enter just "js" (not js0 or js1) to get two joysticks to work.

---

### Post by DoktorSeven on 2007-09-07
If both joysticks are accessible as /dev/input/js* then XMAME should have no problem using them both; did you go into the game configuration screen (TAB) and ensure the second joystick was set up correctly?

I also recommend that you use KXMAME instead of gxmame.  KXMAME is much more stable and works better.

---

