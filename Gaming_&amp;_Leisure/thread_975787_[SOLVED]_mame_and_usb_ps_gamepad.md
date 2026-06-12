---
title: "[SOLVED] mame and usb ps gamepad"
date: 2008-11-08
forum: Gaming &amp; Leisure
---

### Post by hellz99 on 2008-11-08
i'm running 8.10, xmame-sdl and kxmame.  
Using a PS (playstation) controller with a USB adapter. 

In games, all of the buttons work but the directional pad does not.  I'm run jscal and jstest.  It shows that everything works fine using those tools.  

Any insight?

---

### Post by FranMichaels on 2008-11-09
Hmm, never used jscal or jstest. 
But, is there an analog button on your playstation controller? That should solve it if I'm understanding the problem correctly.

Also, if you want a version of mame up to date for ubuntu, try sdlmame.

---

### Post by BigSilly on 2008-11-09
I'm sure in KXMame you have to set your pad manually as /dev/js0 in the options, otherwise things go wrong with your controls. Can you check that, or am I off base?

---

### Post by hellz99 on 2008-11-09
Fran:   
[LIST]
[*]I've tried it with the analog button both on and off.  It should be off to use the D-pad.  So that's not it, but t
[*]The packages I have installed are: mame-sdl, mame-common and kxmane.  I dont see one exactly called sdlmame, but I think it's the same as mame-sdl?
[/LIST]

BigSilly:
In kxmame I have my pad set as /dev/input/js0
This seems to be the correct one, since pstest shows when buttons are pressed, and when mame is running the A,B,X,Y, etc buttons all work, it's just the D-pad that doesn't.

Any one else having similar problems?

---

### Post by BigSilly on 2008-11-09
Does your pad have a button that you can press to select between analogue and digital? Sometimes, such as when I use Mandriva, I have to deselect the analogue setting on my joypad or the D-pad won't work. Also, some people have complained in the past that having JScal installed causes more problems than it solves. Maybe it's causing an issue for you here?

---

### Post by hellz99 on 2008-11-09
Well, it seems to work.  This is what I did:
-uninstalled packages: joystick & jscalibrate
-reboot (didn't work until I did this)
-turn on the Analog button. I'm not using the analog sticks, but for some reason I need it turned on.

---

### Post by BigSilly on 2008-11-09
Brilliant. Glad you got it going. Like I say, I have heard that JSCal can be problematic, but I don't know why this is. Rebooting isn't entirely unusual in this instance.

On my pad, if the light is on then the analogue is in use. Off it's the D-pad. Ubuntu has been always been excellent with my pads.

Mark your thread as solved, so other gamers can benefit from the solution you posted. :)

---

### Post by Derosian on 2008-12-30
Thank you this fixed my exact problem I was having too!

---

