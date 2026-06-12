---
title: "How can I switch between joystick and gamepad?"
date: 2008-04-26
forum: Gaming &amp; Leisure
---

### Post by harlock74 on 2008-04-26
Can anyone help me with this one? I have a microsoft sidewinder gamepad and a logitech joystick which I can get both of them working 100% individually. I'm also running Beryl (can't get Compiz to work on my system) and it's Ubuntu 7.10.

I would like to be able to do the following via a shortcut on my desktop:

1. Turn off Beryl.
2. Set the correct controller for the game (gamepad or joystick)
3. Start the game
4. When the game is exited, turn Beryl back on.

Thanks for any help.

---

### Post by acoustibop on 2008-04-26
Your two controllers will probably be configured as /dev/input/js0 and /dev/input/js1, harlock74.  Try pointing the game at whichever is appropriate.  You may need to edit the game's configuration if it doesn't offer you a choice.

If your game doesn't offer a choice of controllers and there isn't an option to enter a path to the controller in its configuration, try putting a symlink in /dev to whichever controller you want to use (call it js0), as that's where many non-configurable games will look for the controller.  You'll probably need to write a script to change the symlink to whichever controller you want to use if you want to change your choice, though.

---

