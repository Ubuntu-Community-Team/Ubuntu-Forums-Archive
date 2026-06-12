---
title: "Logitech Dual Action pad plugin problem in epsxe and mupen64."
date: 2007-09-25
forum: Gaming &amp; Leisure
---

### Post by Opeth on 2007-09-25
First off, these are my specifications...

Dell Inspiron E1505
Intel Duo Core 2.0GHz (The T2500 processor)
2GB RAM @ 667MHz
ATI Mobility Radeon x1400 (128mb)
100GB 7200rpm hard drive

I'm using Ubuntu Edgy 6.10.
ammoQ's padJoy Joy Device Driver 0.8 (this is the gamepad plugin that I'm using)
I'm using the Logitech Dual Action pad, as seen here...
[http://www.kustompcs.co.uk/acatalog/4707.jpg](http://www.kustompcs.co.uk/acatalog/4707.jpg)

Okay, so, I finally got it to where the analog sticks and d-pad are working. Then, I tried to map the controls. For both of these emulators, whenever I try to map the analog sticks to a button, as soon as I click another button to map it, it closes out and just uses the previous button. 

Say if I want to use the right analog stick, going to the left side, for one button. It does that. But as soon as I click on another button, the window closes quickly and uses the right analog stick going to the left side. On Mupen64, this problem is easily fixed. However, on epsxe, only one button can be assigned to a button, so it replaces what I just did with a "???" without the quotes. It's impossible to fix using the GUI, because it just goes back and forth with the ???.

So I tried to manually edit the configuration file, but for some reason, my configuration just keeps getting reset. Then I noticed that no  matter what I did in the GUI plugin menu, it was always reset back to the default.

1) Why does it reset?
2) Why does it automatically close the window and use the previous button whenever I try to program analog sticks?
3) And finally, I see that you can't use the d-pad with Snes9x, so is there any way to transfer my saves from Snes9x to Zsnes? 

Thanks!

(Using epsxe 1.6.0 and Mupen64 0.5 both for Linux)

---

### Post by acoustibop on 2007-09-25
I finally wound up configuring the controller in ePSXe by editing the configuration file, Opeth.  However, I hardly use it any more as there's a much better Playstation emulator, [pSX]("http://psxemulator.gazaxian.com/").  Very easy to install and configure, as well - and being pluginless, no mucking about trying to find the right ones and getting them to work.

---

### Post by Opeth on 2007-09-25
Thanks for the reply. I tried to install that one other emulator that you posted about, but for some reason, the executable file won't open.

Anyway, could you (or somebody else) please post your epsxe gamepad configuration file? I'd like it to replicate the original Playstation controller as much as possible. 

Thanks.

---

### Post by acoustibop on 2007-09-26
I'm surprised you couldn't get pSX running, Opeth - although, come to thinkof it, there is one library you need: libgtkglext1.  It's in the repositories (Universe, I think).

Here's my padjoy.cfg file:

```
[general]
pcsx_style      = 1
use_threads     = 1
use_analog      = 1
[pad 1]
devicefilename  = /dev/input/js0
minzero = -250
maxzero = 250
event_l2       = B0P6
event_r2       = B0P7
event_l1       = B0P4
event_r1       = B0P5
event_triangle = B0P3
event_circle   = B0P2
event_cross    = B0P1
event_square   = B0P0
event_select   = B0P8
event_lanalog  = B0P10
event_ranalog  = B0P11
event_start    = B0P9
event_up       = A0P5-
event_right    = A0P4+
event_down     = A0P5+
event_left     = A0P4-
event_lanax    = X0P0v0
event_lanay    = X0P1v0
event_ranax    = X0P2v0
event_ranay    = X0P3v0
[macro 1]
event_launch  = ???
events        =
interval      =
[macro 2]
event_launch  = ???
events        =
interval      =
[macro 3]
event_launch  = ???
events        =
interval      =
[pad 2]
devicefilename  = 
minzero = -250
maxzero = 250
event_l2       = ???
event_r2       = ???
event_l1       = ???
event_r1       = ???
event_triangle = ???
event_circle   = ???
event_cross    = ???
event_square   = ???
event_select   = ???
event_lanalog  = ???
event_ranalog  = ???
event_start    = ???
event_up       = ???
event_right    = ???
event_down     = ???
event_left     = ???
event_lanax    = ???
event_lanay    = ???
event_ranax    = ???
event_ranay    = ???
[macro 1]
event_launch  = ???
events        =
interval      =
[macro 2]
event_launch  = ???
events        =
interval      =
[macro 3]
event_launch  = ???
events        =
interval      =
```

Note that, not only do you need analog selected, you also need PCSX selected for Emulation.  You also need to start ePSXe with the -analog switch.

Unfortunately, unlike the Windows version, you can't switch between analog and digital modes.  You have to start the emulator either with or without the -analog switch and the only way to switch is to stop the emulator and restart it.

---

### Post by dfreer on 2007-09-26
As for transfering your saved games, snes9x and zsnes save the games the same way, in a *.srm file (note, this is for saved games and NOT saved states). As long as you use the *.srm's, they should work in both zsnes and snes9x.

I have that exact same controller, except mine is the model with the Mode switch right above the left analog stick. It works perfectly in zsnes and pSX. It also worked in ePSXe and Mupen64 back in the day, although it's been awhile and I don't remember if I had to do anything special to get it to work (although I doubt it).

---

### Post by acoustibop on 2007-09-26
If it has the Mode switch, it's a Rumblepad 2, not a Dual Action, dfreer.  I have a Rumblepad 2 as well; it's an excellent controller and works everywhere - although I did have the same problem as the OP in ePSXe with the padjoy plugin.  However, I think this is a problem with the plugin rather than the controller.

I used to have the Dual Action and, unfortunately, it was one of the ones that the analog sticks went after a while.  I understand this problem doesn't occur any more...

---

### Post by dfreer on 2007-09-27
Not quite true acoustibop ;). There are 3 versions of this controller to my knowledge:
Dual Action Gamepad:
[IMG]http://www.logitech.com/repository/95/jpg/444.1.0.jpg[/IMG]
[http://www.logitech.com/index.cfm/gaming/pc_gaming/gamepads/devices/288&cl=us,en](http://www.logitech.com/index.cfm/gaming/pc_gaming/gamepads/devices/288&cl=us,en)


Dual Action Gamepad w/Mode Switch:
[IMG]http://images.tigerdirect.com/SkuImages/gallery/large/Logitech-DualActionUSB-L23-6376-a.JPG[/IMG]
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1085740&CatId=141](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1085740&CatId=141)


Rumblepad 2 w/Mode Switch and Vibration Switch:
[IMG]http://www.logitech.com/repository/60/jpg/1909.1.0.jpg[/IMG]
[http://www.logitech.com/index.cfm/gaming/pc_gaming/gamepads/devices/264&cl=us,en](http://www.logitech.com/index.cfm/gaming/pc_gaming/gamepads/devices/264&cl=us,en)

I have (2) of the Dual Action Gamepad's with the mode switch, with another on it's way. The first one I've had for a couple years now, and although I rarely use the analog sticks (I don't play many games that use them), I haven't had any problems with them so far.

EDIT: Just realized there is also a Rumblepad 2 that is wireless as well. I might have to try the regular Rumplepad 2 out, does the vibration feature work with pSX in windows acoustibop?

---

### Post by acoustibop on 2007-09-27
Yes, the rumble works excellently in pSX in Windows, dfreer - best and most accurate I've used.

Curiously, though, I've never seen the Mode button version of the Dual Action controller on the [Logitech site]("http://www.logitech.com/index.cfm/gaming/pc_gaming/gamepads/devices/288&cl=us,en").  It wasn't there when I bought one a few years back, and it isn't there now - only the regular one. ???

---

### Post by dfreer on 2007-09-27
I haven't seen it on logitech's site either, but I've only looked recently. I bought my original at a Walmart or some such store a couple of years ago. I specifically bought two more of the Dual Action w/Mode controllers online due to the various rumors I've heard about the Dual Action gamepad's analog sticks failing, and since my original is still good...
I assume, since logitech is no longer carrying the Dual Action w/mode, is that it is an older discontinued model. Don't know why, I guess they figure people don't use it?

@Opeth - I just tried out mupen64 again and replicated your error. Basically what happens, when trying to map the N64 to the Logitech Game Pad things work ok until you map an Axis (left or right analog sticks, not the D-Pad) to any button on the N64. The very first axis will map correctly, but when you click to map another, it will map the previous axis to that key (or perhaps as you suggested, it may be only 1 axis. IDK). It only does this once, so basically what you end up doing is for every axis except the first one, you set it twice. No biggie, it's annoying but what are you going to do? :shrug:
Another thing to look out for is if you map an axis, and THEN map a keypress on your gamepad. It will do the above, but then you'll have both the button and the axis corresponding to the same keypress (for example, in 007 everytime I would turn left, my gun would fire). When this happens, just hover the mouse over the key in question in the GUI, and then press the <Delete> key. DON'T map the delete key, just hover and press and it should erase that key's mapping. Hope that isn't too confusing!

---

### Post by Opeth on 2007-09-28
Thanks a lot guys. I never did get pSX to work, even with that extra file, but I've fixed all of my problems pretty much.

Thanks again! You guys are awesome! :D

---

