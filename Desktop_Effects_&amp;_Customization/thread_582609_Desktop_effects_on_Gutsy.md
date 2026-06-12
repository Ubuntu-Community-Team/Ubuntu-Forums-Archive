---
title: "Desktop effects on Gutsy"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by abhilash82 on 2007-10-20
I have upgraded Gutsy successfully and I am trying to enable the desktop effects in the Appearance window. I lost my window border when I selected the option "Normal" in the Visual effects tab. When I selected "Extra" the settings came back to "None" automatically after some time. My PC is based on Intel 865 motherboard with on-board graphics card and I have used compiz successfully in Feisty. I would like to know if I can use the desktop effects at least in the "Normal" mode?

Another thing is that I am not able to select Appearance->Windows settings and it gives me the error **"Cannot start the preferences application for your window manager"** and **"Window manager "compiz" has not registered a configuration tool"** messages when I am using Visual effects in the Normal mode. I am able to access the window settings in the "None" mode of Visual effects.

I came to know that the"i810" driver is white-listed with Compiz and the Visual effects must work with the hardware.
:(

---

### Post by abhilash82 on 2007-10-23
Has anyone come across the same problem with your Gutsy installation with intel motherboards? Can anyone help me out on this?
:confused:

---

### Post by clevermacia on 2007-10-27
hey, yeah i was having the same problem i sort of fixed it though. So what I did was just went into the synaptic package manager and completely removed anything that had to do with compiz. Then I re-installed all the compiz stuff, then now you should have "advance desktop effect settings" under system < preferences . then in there you can mess with all of the old stuff from beryl. If it get's laggy, cuz i was having problems with extremely slow performance.. so i fixed that by toggeling the water drops by pushing shift+f9 and you might have to enable that in your settings too. I don't know why that works but for now i'm just using ubuntu with water drops all over my screen, which isn't too bad but everything runs really smoothly now.

---

### Post by handzmonkey on 2007-10-27
I have an intel 950 gma and when I tried to upgrade from 7.04 to 7.10 the basic effects would work.  But eventually the effects like expo (the show all windows effect) would work for 3 instances then die.  Also I would get the video issues.Unless i specified X11 output  for Xine and other video players they would just die when I tried to run them.  Sadly I had less problems with compiz on 7.04 than i did with 7.10. Note that I tired using both drivers with X11 (i810 and intel) and there really wasn't any difference.  From what I have read the integrated video cards just don't cut it for anything advanced.

---

### Post by PCZahra on 2007-10-28
I can't get water effects to work. pretty much everything else works, but not water. I turned it on, hit shift+f9 and nothing happened. the initiate shortcut was disabled, so I put ctrl+shift+f9, hit that, nothing happened, hit shift+f9 again, nothing happened. this is the only effect that does absolutely nothing.

Update:
it does do something, apparently whenever I have it on I can't click the desktop switcher thing on the lower panel or both panels and sometimes even all the windows and desktop icons will disappear

---

### Post by clevermacia on 2007-10-29
yeah.. unfortunately i regret upgrading to gutsy. The new compiz fusion has actually done worse for me than compiz+beryl+xgl on feisty fawn.. linux is pulling a microsoft.. jk but seriously i've wasted so much time trying to fix problems AFTER i upgraded, when feisty fawn ran smoothly with even cooler effects.. eventually there will be some posts from some more savvy users.

---

### Post by shijirou on 2007-10-29
I miss beryl too. But still lets see if they're gonna have any updates for compiz. I had to disable every effect on my PC just to make Gutsy to work back during the RC betas and now it wont even boot. Lol. Anyway, I guess it depends on the PC you have. Gutsy is fine on my laptop, fine on my older Pentium 4, but somehow screwey on my higher end gaming PC.

---

