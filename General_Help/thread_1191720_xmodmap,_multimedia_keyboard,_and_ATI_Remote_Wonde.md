---
title: "xmodmap, multimedia keyboard, and ATI Remote Wonder"
date: 2009-06-19
forum: General Help
---

### Post by glancep on 2009-06-19
Kubuntu 9.04

I have been trying to get my ATI Remote Wonder to work nicely on my system that also includes a multimedia keyboard.  The remote was always successfully recognized by the system, and the volume and mouse move/buttons have always worked great.  The audio keys: not so much.  Apparently they return different keycodes than the multimedia keys on my keyboard for the same function.  So I have been trying to use xmodmap to remap the remote keys to match the XF86Audio* keysyms that the keyboard uses.  Yesterday I came across a thread suggesting to add the following to the xorg.conf:

Option  "AutoAddDevices" "False"

This was supposedly because of the way the newer X version handles input and without it, any xmodmap entries would be ignored (and also I had to change my xmodmap startup command to run through a terminal, instead of just a script in autostart).

Anyway, last night I thought I had it all mapped properly and everything was working great... the play/next/prev/etc all worked perfectly from both the remote and keyboard.  Well, when I booted up this morning, no dice.  The keyboard still works fine, but the audio keys on the remote do nothing!! ::frustration::  I used xev to see if my xmodmap was set up and it was.... all of the keys on the remote present the exact same XF86Audio* commands as their keyboard counterparts, just like last night.  The only thing now is that Amarok is ignoring them when coming from the remote.  Not that I blame Amarok--when I set up any other system shortcut to use any of those buttons, it also only works from the keyboard.  What is really weird is that I can even set up the shortcut with the remote... it accepts the button in the shortcut dialog, but then when I press it after assigning, it does nothing.  The keyboard will work, though!!

While I still have hair that I have not torn out, can someone offer some guidance here?  If you need anymore info to diagnose, just ask and I'll post it.

Thanks so much,
Gideon

---

### Post by glancep on 2009-06-19
Any X input/xmodmap experts out there?  Even if you just have an idea of somewhere I might begin looking... or something I could use to diagnose how the system can see a difference between the two keys when xev is showing them both as the same mapping (the keycodes are still different, but I would hope and assume that shortcuts are based on the key shown when you set the shortcut--keysym I think--not the keycode).

Anyone?

Thanks a lot,
Gideon

---

