---
title: "Getting gamepad to work with Doomsday jHexen"
date: 2006-06-08
forum: Gaming &amp; Leisure
---

### Post by EReckase on 2006-06-08
I've successfully built Doomsday on my Dapper system, and it runs great - but I'd love to use my Logitech Dual Action controller to play.  I've enabled joystick in the game, and I've run jscalibrator (and have successfully seen the buttons and joysticks work in it) - but I get no response from the gamepad while jHexen is running.  Any ideas on how to get it moving?

---

### Post by Yagisan on 2006-06-08
[QUOTE=EReckase]I've successfully built Doomsday on my Dapper system, and it runs great[/quote]Of course it runs great. I do all *NIX development of it on Dapper. (We do have dapper packages, but they haven't been formally announced as I haven't yet updated all the resource packs from breezy)

[QUOTE=EReckase] - but I'd love to use my Logitech Dual Action controller to play.  I've enabled joystick in the game, and I've run jscalibrator (and have successfully seen the buttons and joysticks work in it) - but I get no response from the gamepad while jHexen is running.  Any ideas on how to get it moving?[/QUOTE]Did you set it up in all three games ? there is a seperate configuration for each game. Just to confirm, You are using 1.9.0beta4 ? Eairlier versions have no joystick support on *NIX.

---

### Post by EReckase on 2006-06-08
Whoops...I'm running 1.8.6.  I'll get the latest version, get it compiled, and let you know.  Thanks!

---

### Post by EReckase on 2006-06-08
1.9.0 beta 4 is SCHWEET!  Gamepad works very well!  Many thanks for letting me know.

It'd be nice if there was a link to the beta from the Doomsday HQ page... :)

---

### Post by Yagisan on 2006-06-09
[QUOTE=EReckase]1.9.0 beta 4 is SCHWEET!  Gamepad works very well!  Many thanks for letting me know.[/quote]When announced, I'd suggest you install the ubuntu packages (details in first link in my sig), as they include some important fixes backported from beta5 development.

[QUOTE=EReckase]It'd be nice if there was a link to the beta from the Doomsday HQ page... :)[/QUOTE]We are conisering applications for the redevelopment of that site see [http://forums.newdoom.com/showthread.php?t=30605](http://forums.newdoom.com/showthread.php?t=30605) for details.

---

### Post by EReckase on 2006-06-10
Well, maybe I spoke too soon.  Given that it's 'joystick' support and not 'gamepad' support, it's not too surprising, but nevertheless, I thought I'd describe my experience.

The digital buttons on my gamepad correspond to the 'x' and 'y' axis of the joystick settings.  I can optionally select the analog joystick on the left to be the 'x' and 'y' axis - but regardless of the settings, I can't figure out how to use both directions of the second analog controller.  There's no way to select a setting for the up/down direction of that stick - only l/r.

I assume this can't be done, which is fine - the rest of the controls seem to work OK...I might try my Nostromo and see how that goes - shouldn't need any joystick support for that, necessarily.

Thanks!

---

