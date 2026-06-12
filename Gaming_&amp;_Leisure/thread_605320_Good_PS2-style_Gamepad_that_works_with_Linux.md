---
title: "Good PS2-style Gamepad that works with Linux?"
date: 2007-11-06
forum: Gaming &amp; Leisure
---

### Post by enigma_0Z on 2007-11-06
I'm looking for a gamepad that is similar in form factor & buttons to the PS1/2 controller w/ the dual analog sticks to get for my linux boxx

Does anyone know of one that would work for sure? I've seen some of the logitech ones, but I can't remember the names of any of them.

Does anyone know of a good controller that fits that form factor and works with Linux?

By the way, a console-to-usb adapter is not the solution for me.

---

### Post by cogadh on 2007-11-06
Logitech Dual Action. It's identical to the PS2 Dual Shock, but without a rumble function. Works out of the box with Linux.

---

### Post by dfreer on 2007-11-07
+1 for the Logitech Dual Action. Great controller, I have 3 of them.

---

### Post by acoustibop on 2007-11-07
I have a Logitech Rumblepad 2 (wired).  Very similar to the Dual Action, but even better (I've had a Dual Action as well), with rumble (useless in Linux, but the most accurate I've come across in Windows) and a very nifty little Mode switch, which enables you to switch directional pad control to the first analog stick.  So, if you're playing a game without analog support where you'd normally have to use the directional pad, you can use the first analog stick instead.

It's lasted me about three years now, and still good as new.

**Edit:** also works out of the box in Linux.

---

### Post by Naegling23 on 2007-11-07
I have the logitech dual action 2 rumble thinger too.  Works well.

But if your looking for a ps2 controller, why not get a 10 adapter and a ps2 controller?  They work well too.

---

### Post by acoustibop on 2007-11-07
They do sometimes, but results can be very variable.  I hear Gutsy is better than Feisty for PS2 controllers with USB adapters, though.

---

### Post by dfreer on 2007-11-07
> **acoustibop said:**
> I have a Logitech Rumblepad 2 (wired).  Very similar to the Dual Action, but even better (I've had a Dual Action as well), with rumble (useless in Linux, but the most accurate I've come across in Windows) and a very nifty little Mode switch, which enables you to switch directional pad control to the first analog stick.  So, if you're playing a game without analog support where you'd normally have to use the directional pad, you can use the first analog stick instead.

It's lasted me about three years now, and still good as new.

**Edit:** also works out of the box in Linux.

I think I've brought this up before, but there is a Dual Action version from tigerdirect.com that comes with the mode switch as well, it's very useful. Not to mention, a bit cheaper than the Rumblepad (although having rumble in windows would be worth it, if I used windows ;) )

---

### Post by cogadh on 2007-11-07
> **Naegling23 said:**
> But if your looking for a ps2 controller, why not get a 10 adapter and a ps2 controller?  They work well too.
The OP specifically said that wasn't an option.

---

### Post by Steveway on 2007-11-07
I bought a Saitek P990 a few weeks ago.
Works nice, though the "button-programming-program" is not avaiable for Linux.
And I haven't got the Rumble-features to work but I'm sure that should be no big deal to get to work.

---

### Post by dfreer on 2007-11-07
AFAIK, there is no way to get controllers to rumble in linux.

---

### Post by cogadh on 2007-11-07
AFAIK, you are correct. I believe rumble and force feedback abilities are functions of the DirectInput component of DirectX in Windows, so they really can't work in Linux.

---

### Post by greentiger on 2007-11-07
i just use my ps2 controllers with the PS2-to-USB adapter.
works great.

---

### Post by enigma_0Z on 2007-11-08
Thanks for all the input guys. I'm probably going to buy the Logitech dual action. Maybe two. Is there any issues with getting two of them working at the same time? I would assume that they get /dev/input/js0 and /dev/input/js1 ?

---

### Post by dfreer on 2007-11-08
I've used 3 at a time, as previously mentioned. I never actually checked what they get assigned to (other than the first controller will get /dev/input/js0), because they simply worked for me (I can check if needed). Just general FYI's that are more common sense than anything else:
(1) Plug in your controllers first, then start the emulator. Most programs will not be able to use a new USB device until you restart the program, if that makes sense.
(2) When configuring these identical multiple controllers in my emulators, I generally do the following:
[list]
[*]Plug in one controller, start the emulator, configure that controller for Player 1. Close emulator.
[*]While the first controller is still plugged in, plug in the next controller and launch the emulator. Configure it for Player 2. Repeat as needed.
[/list]
Basically, this just makes things easier as to which controller is which. When you play your games, from then on first controller in will always be first player, etc.
(3) In pSX, if you start the emulator with no joypad plugged in, in the controller config it will default to **Device: None**. If you then start the emulator again, with a controller plugged in it will still be set to **Device: None** and you will need to change it back to **Device: Logitech Dual Action Joypad** or whatever your pad is called. The buttons will still be mapped, so you won't have to remap them thankfully.

Eh, that's about all I can think of right now. I like to play **Secret of Mana** on zsnes with 2 friends, and we haven't run into any issues.

---

### Post by BigSilly on 2007-11-08
[I use this pad myself.]("http://www.play.com/PC/PCs/-/673/880/-/3274924/Speed-Link-Strike2-Gamepad-With-Force-Vibration-In-Transparent-Blue/Product.html?searchtype=genre") It's excellent in Linux - works with all my favourite emus (including MAME) and also the 3D shooters and stuff too. So good I bought two!

---

