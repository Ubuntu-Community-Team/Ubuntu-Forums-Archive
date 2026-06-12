---
title: "What Game Controllers/Pads/Joysticks Do You Use?"
date: 2007-08-01
forum: Gaming &amp; Leisure
---

### Post by MutualDisdain on 2007-08-01
I purchased two Game Elments GGE909 controllers from Walmart. At first everything was pretty good, but now that I am playing games regularly I am noticing that the controllers work inconsistently.

Sometimes buttons stop working, and others the entire controller doesn't work. I am guessing this is a driver issue, but I am considering taking them back since I still have the receipt and boxes. I've noticed a lot of Windows users complaining about the Game Elements controllers online.

What game controllers do you use with Ubuntu, and how well do they work?  I am interested in purchasing a controller that a lot of people have had success with.

Thanks

---

### Post by primski on 2007-08-01
well, i got a logitech rumblepad2 gamepad, haven't really tested it, couse the only game i play is PES6 and doesn't work in ubuntu :s 
The jscalibrator or whatever it is, shows the gamepad works great, all buttons and axis, so its hard to tell how it does it the games.

other than that its a great gamepad and definitely a recommendation

---

### Post by DoktorSeven on 2007-08-01
An old MS Sidewinder pad (gameport version!  Old, I know :) ) and a Playstation1 controller (through a USB->PS converter thingy).  Both work perfectly well though I have to load the "sidewinder" module and blacklist the "analog" one else the Sidewinder won't work.

---

### Post by cogadh on 2007-08-01
Logitech Dual Action gamepad and a Logitech Wingman Extreme joystick. Both work great.

---

### Post by BigSilly on 2007-08-01
I have a Joytech Neo USB dual analogue pad, and a Speedlink Strike2 pad that's also dual analogue. Both work pretty good in Linux. In fact, I think the only game that I can't get to recognise the pad as it should is GridWars. It claims to have dual analogue support, but the config tool does nothing and I can't get it to work. If anyone has any help here it'd be most appreciated.

Otherwise I can't say I have the same problems as you I'm afraid. It sounds like it might be the pads rather than the Linux drivers, especially if Windows users are complaining too.

---

### Post by shynko on 2007-08-01
I had the same problem with the gce909 controller playing supertux earlier  though the controller worked like a charm on windows with emulators anyway never tryed the  controller on a game on windows.

---

### Post by acoustibop on 2007-08-01
I also have a Logitech RumblePad 2 (wired) and it's an excellent controller - mostly I use it for emulators.  Very nice action.

I usually make sure it's plugged in when I install Ubuntu and it's recognised 'out-of-the-box.'  After using it for a year, at least, it's showing no signs of failure of the analog sticks, which unfortunately seemed to affect some other Logitech controllers, particularly the Dual Action pad.

It has a neat little wrinkle in that it has a Mode button that interchanges the functions of the directional pad and the first analog stick - so even in a digital controller-only game, I can still use the stick for directional control.

I've had no problems getting it recognised in games/emulators although, of course, some emulators can be fiddly to get right.  Currently I have it working happily with pSX, ePSXe (digital only), ZSNES, GENS and Mupen64.

---

### Post by mccord on 2007-08-16
> **BigSilly said:**
> I have a Joytech Neo USB dual analogue pad, and a Speedlink Strike2 pad that's also dual analogue. Both work pretty good in Linux. In fact, I think the only game that I can't get to recognise the pad as it should is GridWars. It claims to have dual analogue support, but the config tool does nothing and I can't get it to work. If anyone has any help here it'd be most appreciated.

hi 
i had the same problem with my logitech dual action joypad and grid wars.
grid wars looks for /dev/js0 for the first gamepad, but my pad was under /dev/input/js0
a simple 'sudo ln -s /dev/input/js0 /dev/js0' (the command creates a symbolic link) solved the problem and the pad works now with grid wars :)

---

### Post by beeldings on 2007-08-16
I use a [Saitek P990 Dual Analog pad](http://www.saitekusa.com/usa/prod/p990.htm). It pretty much works out of the box, but I had to use jstest to retrieve the controller parameters so that I could enable the pad in Cedega. I can play Madden NFL 07 as well as zSNES using this pad without any problems.

---

### Post by bouncingmolar on 2007-10-28
what games do you guys use your joysticks for?

---

### Post by FRuMMaGe on 2007-10-28
I use the Logitech Precision controller. It is probably the simplist usb controller around. It is basically the same as a PSX controller but with a nicer feel to it. Works out of the box in Ubuntu as well :)

The only bad thing about it is the lack of an analogue stick, but at £5 brand new in Gamestation I can't complain! :)

---

### Post by primski on 2007-10-29
> **bouncingmolar said:**
> what games do you guys use your joysticks for?

on ubutnu? nothing really, the only game i play is Pro evolution soccer, and that doesnt work on ubuntu :s

---

### Post by swimb on 2008-03-16
> **mccord said:**
> hi 
i had the same problem with my logitech dual action joypad and grid wars.
grid wars looks for /dev/js0 for the first gamepad, but my pad was under /dev/input/js0
a simple 'sudo ln -s /dev/input/js0 /dev/js0' (the command creates a symbolic link) solved the problem and the pad works now with grid wars :)

How can I make this stick? After a reboot it needs to be re-entered.

---

### Post by grossaffe on 2008-03-16
I have a logitech RumblePad2, but haven't exactly used it for anything in ubuntu yet.  i've been trying to get it to work with Wolfenstein: Enemy Territory, but no luck so far.  I also have an SNES->PC adaptor i built that i use for my emulator games; up to five controllers.  At some point, i may use it for some arcade-style games as well since i have one of them SNES arcade controllers.

---

### Post by desertboy on 2008-03-17
Xbox360 pad (There's a thread in the forums about how to get them to work), PS3 pad (Which just worked but has to be plugged in) and a flight joystick (Which just worked). Games on the other hand seem not to like pads in linux, flight gear is alright and emu's seem ok but I couldn't get any FPS to work with a pad.

---

### Post by grossaffe on 2008-03-17
> **desertboy said:**
> Xbox360 pad (There's a thread in the forums about how to get them to work), PS3 pad (Which just worked but has to be plugged in) and a flight joystick (Which just worked). Games on the other hand seem not to like pads in linux, flight gear is alright and emu's seem ok but I couldn't get any FPS to work with a pad.

yeah, its pretty annoying since i'm a console person.  THE thing i really liked about my logitech controller when i used windows was the software that went with it.  qjoypad tries to be what logitech gaming software is.

---

### Post by Ferrat on 2008-03-17
I use a simple Xbox controll ghetto moded to USB works great, to good infact since it has preasure sensitive buttons and using it for Mupen64 specially that has a hard time telling a light pres on one button from a hard pres on a another ^^ but all and all really good.

---

### Post by themacmeister on 2008-03-18
I am using a Logitech Dual-Action USB, twin analog (PSX Dual-Shock, without rumble). Very happy with it, needs Joystick package to work fully, also needs symlink /dev/js0 from /dev/input/js0

Only downside is they are fragile (compared to PSX controller), and need to be purchased every 2 years or so - but they are cheap...

---

### Post by acoustibop on 2008-03-18
Try the Logitech RumblePad 2, themacmeister - it's the next model up, and has a much better build quality than the Dual Action.

It also has a rather nice wrinkle in a Mode button - this changes functions between the directional pad and the first analog stick, so when you're playing games that only have digital control, you can still use the analog stick.

It also has very accurate rumble - but, of course, that's a moot point in Linux... :(

---

### Post by heartburnkid on 2008-03-18
I use a pair of third-party PS2 pads through a USB converter (specifically, [this one]("http://www.play-asia.com/paOS-13-71-6m-49-en-70-1b5.html") ).  One of them is a Nyko  iType2, which is designed for MMO games and has a built-in QWERTY keyboard.  This comes in handy more often than you think.  Both Ubuntu and Windows read the keyboard as a standard USB keyboard.

---

### Post by grossaffe on 2008-03-18
> **acoustibop said:**
> Try the Logitech RumblePad 2, themacmeister - it's the next model up, and has a much better build quality than the Dual Action.

It also has a rather nice wrinkle in a Mode button - this changes functions between the directional pad and the first analog stick, so when you're playing games that only have digital control, you can still use the analog stick.

It also has very accurate rumble - but, of course, that's a moot point in Linux... :(

i've never actually played a game that took advantage of its rumble capability.  i kinda hoped that project64 (on windows :() would with the rumblepak option.

---

### Post by pkkid on 2008-03-20
I use PS2 controller with a converter to USB called: "Super Dual Box Pro".  I don't even own a PS2, but thought these were the best controllers ever made and went with it.  Works great! :)

---

### Post by grossaffe on 2008-03-21
> **pkkid said:**
> I use PS2 controller with a converter to USB called: "Super Dual Box Pro".  I don't even own a PS2, but thought these were the best controllers ever made and went with it.  Works great! :)

i didn't like the ps2 controllers to be completely honest.  i prefer xbox360 and gamecube controllers.  they both had the joysticks in a better location and the depth-sensative triggers were another plus.

---

### Post by cisforcojo on 2008-03-22
I have a very very cheap Chinese controller that I bought for 15 yuan (about $2) and has "WELCOM" on the front of it. It works well enough but SDL plugins have a terrible time detecting the different axes or the d-pad (it's analog). I effectively can't use it at all in Mupen64 (can't get the Wingman64 plugin to work at all, gtk errors) but pSX works perfectly.

---

### Post by mutation on 2008-03-22
I love my Thrustmaster F16, its old but works perfect,had it since about 86-87 and still works perfect, the dos prgramming app works in dosbox, so until i break it i'm not repplacing it.

[IMG]http://www.empirenet.com/f2comp/f16flcs.jpg[/IMG]

---

### Post by Darganot on 2008-03-22
[Logitech Chillstream]("http://www.logitech.com/index.cfm/gaming/pc_gaming/gamepads/devices/292&cl=us,en")

It's basically a copy of a 360 controller with a fan in the middle.  The fan is loud but the controller is solid.  The wife picked it up for me at Wal Mart as a matter of fact.

There's a thread [here]("http://ubuntuforums.org/showthread.php?t=428469") for help installing the driver - same one used for the 360 controller.

Personally, I played games on consoles for years and never thought gaming on a PC could be the same *because* of the controller.  Now I play those same games on linux...

---

### Post by cdsboy on 2008-03-22
I'm runnin a [Sega Virtua Stick High Grade]("http://www.play-asia.com/paOS-13-71-zl-49-en-70-1rjw.html"). And its all for TETRIS!!! Works flawlessly with [Texmaster]("http://www.tetrisconcept.com/forum/viewtopic.php?t=893")

---

### Post by Sisyphus48 on 2008-08-01
I just bought a Logitech Attack3 for $30 to play Nexuiz.  I haven't been able to get it to work:confused: acceptably so I'm taking it back tomorrow.

---

### Post by jimi_hendrix on 2008-08-01
i use a good old laptop mouse pad and a keyboard

its a pain when i play starfox and such and a mouse gives you better control when sniping guys from the other side of the map but u learn to live with it

---

### Post by grossaffe on 2008-08-01
I've got a Logitech Rumblepad2.  Mostly use that for Windows or my laptop since there aren't any really good programs for mapping the joysticks (qjoypad could be so much better).

Wiimotes.  Used pretty much exclusively in Windows on my laptop, perfect for N64 games such as Ocarina of Time (using TP controls).  I just wish there were programs for linux that worked as well with the wiimote as GlovePIE does for Windows since I find it much easier to connect a wiimote in Ubuntu than in Windows (Windows is very inconsistant with connecting to them).

And the the controllers I use the most often nowadays: 5-port SNES controller bay.  Works perfectly for my desktop's parallel port and I use it for all of my emulator games.

edit: apparently I already posted in this thread before...

---

### Post by desertboy on 2008-08-03
PS3 pad works fine OOTB as long as it's plugged.

---

### Post by Rhubarb on 2008-08-03
I'm using a wiimote and the wiimote clasic controller.
Works fine as a joystick / mouse / keyboard in Ubuntu :D

---

### Post by HansKisaragi on 2008-08-03
Smart Joy + Ps2 Controller for all my emulation.-

---

### Post by 1337 on 2008-08-05
I got some cheap noname usb gamepad which is detected as "DragonRise Inc. Generic USB Joystick", with two analog sticks looking kinda similar to dualshock and it worked out of the box, without vibrations tho but I think not too many game controllers on linux support that. AFAIK lot's of noname dualshock clones use Dragonrise chips that can be helpful for some ppl. I'm using it mainly for emulators f.e. Mednafen and pSX.

Regards

---

### Post by danny_galaga on 2008-08-16
another logitec precision user here. it must be the most compatible controller around (",)

but id like to pick up an analog one for N64 emulation. hopefully the logitec works.

---

### Post by CyberCod on 2008-09-28
I've used several in the past couple years.

Thrustmaster Dual Power analog (PSX knockoff but built like a tank)
   Best I've used, highly recommended.  Mine is 5 years old and just recently got a short in the cable.  I'm going to have to splice it, but then I expect it'll last a few more years.  Works great in Ubuntu.


Game-Elements Recoil pad (another PSX knockoff, D-pad is twitchy and impossible to use without hitting a diagonal...and the USB cable is cheap)  
    Works fine in Ubuntu but the pad itself is cheap.  The cable is flat (so it can wind itself up inside the controller) and tears much too easily... not to mention that it curls like an old phone cord.  Very springy, very annoying.  Not recommended.  My son killed one of these in about 4 months when he was 3.


and I also use a regular PS2 controller via a cheap Chinese-made adapter...
packaging just says "USB Super Convertor for PsX Controller and USB Connect 2 in 1"  It takes two PS(x) controllers and pipes them into one USB slot.  So far I've only tried it with one plugged in.  It works decently well in Ubuntu, though I have weird issues with the analog sticks.

---

### Post by klikklak on 2008-09-28
Has anyone used a Saulabi arcade stick or a dance mat from play-asia?  I've been thinking about getting those and I'd like to know about compatibility.

---

### Post by fortAlamo on 2008-10-09
> **1337 said:**
> I got some cheap noname usb gamepad which is detected as "DragonRise Inc. Generic USB Joystick"

same controller here,works fine in urban terror.



BUT I can't find out how to configure ( scph1010/1150/1200  ?!any option seems useless ) and use it in pSX :(

---

