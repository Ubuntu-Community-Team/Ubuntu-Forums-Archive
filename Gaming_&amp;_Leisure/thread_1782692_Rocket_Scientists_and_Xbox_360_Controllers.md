---
title: "Rocket Scientists and Xbox 360 Controllers"
date: 2011-06-14
forum: Gaming &amp; Leisure
---

### Post by PStephens7 on 2011-06-14
I have a wired Xbox 360 controller. I've found many tutorials on how to install it and I read of many people having much success. They can go into their games and just enjoy them with a controller in their hands. Turns out though, I have to be a rocket scientist to do this myself. 
My uncle actually is a rocket scientist. When I was younger he would just give me $20 for no reason when I'd see him. He's pretty good with computers it seems, and he just might be able to do this. However, as I said before, I am not a rocket scientist. So I spend hours googling how to use my wired Xbox 360 controller and try many different things, which all do absolutely nothing for me.
Alright, well here's my issue. My computer recognizes it, but when I press down on the left analog stick, the mouse goes up to the left corner of the screen. I also discovered that the right-trigger makes the mouse go down. I think start clicks. How to change this? Of course, I have no idea.
Now I'm not necessarily asking for help. It seems many people have gone out of their way making tutorials for others to get their wired Xbox 360 controllers working on their computer. If this gets deleted, I don't really care. I just thought to myself, "Hey, why not go post on these forums myself instead of just googling around? But instead, I'll post a new thread sarcastically voicing my frustration with the high skill level required to actually do basic things in Linux." It seemed like a swell idea. 
Hey, I don't like Windows either, and I'm not going to go back to using it, but I must admit, Windows is a whole lot more user-friendly.

Signed, Philip Stephens. aka, the Philibuster

---

### Post by HansRuesch on 2011-06-16
Look for a file called '50-joystick.conf'. It should be located at '/usr/share/X11/xorg.conf.d/'. Open it and change the options "StartMouseEnabled" and "StartKeysEnabled" to "False". If they aren't there, add them yourself. The file should end up looking like this:

```

Section "InputClass"
    Identifier "joystick catchall"
    MatchIsJoystick "on"
    MatchDevicePath "/dev/input/event*"
    Driver "joystick"
    Option "StartKeysEnabled" "False"
    Option "StartMouseEnabled" "False"
EndSection

```
Reboot afterwards. That should do it; worked for me, at least.

Good luck.

---

