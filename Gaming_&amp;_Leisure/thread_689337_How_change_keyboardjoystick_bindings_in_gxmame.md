---
title: "How change keyboard/joystick bindings in gxmame?"
date: 2008-02-06
forum: Gaming &amp; Leisure
---

### Post by christian.convey on 2008-02-06
I'm new to the whole Mame thing, so maybe this is a dumb question.

Suppose that someone has a Ubuntu 7.10 PC.  It has a keyboard (as you might expect), and a PlayStation 3 sixaxis controller plugged into the USB port.  The PS/3 controller shows up as /dev/input/js0, and KDE's Joystick program shows the controller working just fine.

Now suppose one installs a game like Mortal Kombat into mame.  It's not clear how the keyboard's keys, or the joystick's buttons, map into Mortal Kombat's joysticks and buttons.  The default mappings are appear very broken and unusable.

---

### Post by disturbedite on 2008-02-06
i'd recommend using kxmame instead.  its faster.  also, xmame has been dead for a long time & is at mame 0.106, while sdlmame (a newer mame port) is at 0.123.  its synced with mainline mame.  (in other words, it stays up-to-date).
you can grab a deb package of kxmame from here:
[http://sdcofer.googlepages.com/home](http://sdcofer.googlepages.com/home)
(don't use the version of kxmame from the ubuntu repo, its outdated & doesn't support sdlmame).

sdlmame is now in the ubuntu repo, so you should be able to install it from your package manager, but if not, you can get deb packages of it here:
[http://wallyweek.altervista.org/index.php](http://wallyweek.altervista.org/index.php)

with sdlmame, you can configure the keys through the main menu or in the config file.

---

### Post by DoktorSeven on 2008-02-06
MK's mapping is very obtuse, but here's how it works:

Button 1: High Punch
Button 2: Block
Button 3: High Kick
Button 4: Low Punch
Button 5: Low Kick
Button 6: nothing (MK1/2), Run (MK3).

---

### Post by christian.convey on 2008-02-06
> **disturbedite said:**
> i'd recommend using kxmame instead.  its faster.  also, xmame has been dead for a long time & is at mame 0.106, while sdlmame (a newer mame port) is at 0.123.  its synced with upstream mame.  (in other words, it stays up-to-date).
you can grab a deb package of kxmame from here:
[http://sdcofer.googlepages.com/home](http://sdcofer.googlepages.com/home)
(don't use the version of kxmame from the ubuntu repo, its outdated & doesn't support sdlmame).

sdlmame is now in the ubuntu repo, so you should be able to install it from your package manager, but if not, you can get deb packages of it here:
[http://wallyweek.altervista.org/index.php](http://wallyweek.altervista.org/index.php)

with sdlmame, you can configure the keys through the main menu or in the config file.

Thanks.  I followed your advice and installed kxgame and xmame-sdl.  I found the properties tab in kxmame where I can mention the use of keyboard, mouse, and joystick. 

But where can I specify details such as "this joystick button number maps to this game button" or "this keyboard key maps to this game button"?

Thanks,
Christian

---

### Post by frenchn00b on 2008-02-06
i got it with xmame.sdl

[http://ubuntuforums.org/showthread.php?t=679813&highlight=xmame+gamepads](http://ubuntuforums.org/showthread.php?t=679813&highlight=xmame+gamepads)

---

### Post by christian.convey on 2008-02-06
> **DoktorSeven said:**
> MK's mapping is very obtuse, but here's how it works:

Button 1: High Punch
Button 2: Block
Button 3: High Kick
Button 4: Low Punch
Button 5: Low Kick
Button 6: nothing (MK1/2), Run (MK3).
Thanks, but how to buttons 1-6 map to my keyboard and/or PS/3 sixaxis controller?

---

### Post by disturbedite on 2008-02-07
you guys *did not* follow my advice.  i said *do not* use xmame-sdl.  SDLMAME is the right program, NOT xmame-sdl...

---

### Post by frenchn00b on 2008-02-07
> **disturbedite said:**
> you gusy *did not* follow my advice.  i said *do not* use xmame-sdl.  SDLMAME is the right program, NOT xmame-sdl...

ahhh I misunderstood. sorry.

SDLMAME, hence this : [http://wallyweek.altervista.org/](http://wallyweek.altervista.org/) (?)
(no idea really why so much mame programs)

---

### Post by disturbedite on 2008-02-08
> **frenchn00b said:**
> ahhh I misunderstood. sorry.

SDLMAME, hence this : [http://wallyweek.altervista.org/](http://wallyweek.altervista.org/) (?)
(no idea really why so much mame programs)
yes, that is the program/package i wrote about.
i'll explain why there are "so much mame programs".
xmame development stopped (the project died) a long time ago.
sdlmame is a mame port to sdl.  it is simply mame made to run sdl, so its always up-to-date with mainline mame.

---

