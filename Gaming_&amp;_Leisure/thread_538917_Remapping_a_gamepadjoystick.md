---
title: "Remapping a gamepad/joystick"
date: 2007-08-30
forum: Gaming &amp; Leisure
---

### Post by DeadlyMuffin on 2007-08-30
I would like to remap a USB gamepad so that I can assign which button is  1/2/3/4 instead of having it done automatically. (It's a logitech dual action).

My gamepad works for most things, but each program seems to have a different layout and they tend not to be very configurable.

At this point, the only emulator where I've been able to get the gamepad mapped correctly is zsnes. I just wish zsnes played everything. 

If there's no good way to remap the gamepad itself, can anyone at least suggest a Sega Genesis emulator for ubuntu/linux that allows input configuration like zsnes does?

---

### Post by acoustibop on 2007-08-30
I think quite a few people have got GENS configured by manually editing their configuration file (~/.gens/gens.cfg), DeadlyMuffin.

As an example, the first 6 lines of the Input section of my GENS configuration file are:
[Input]
P1.Type=1
P1.Up=4097
P1.Down=4098
P1.Left=4099
P1.Right=4100

You could try those assignments for a start; if that doesn't work, try setting all the direction settings in GENS to the same direction, then look in the configuration file to see what that direction is read as.  Do the same for the other directions, and then manually insert the appropriate settings in you configuration file.

---

### Post by DeadlyMuffin on 2007-09-01
How do you know which gamepad button corresponds to which code?

---

### Post by acoustibop on 2007-09-01
That's why I suggested setting all the direction settings to the same button, then repeating it for each button, DeadlyMuffin.  Each time, you look in your configuration and you should have the same value assigned for each direction - that way you can find out the value for each button.

---

### Post by stmiller on 2007-09-01
I use a program called [Qjoypad]("http://qjoypad.sourceforge.net/") to map my gamepad buttons in some emulators that do not cooperate.

---

### Post by DeadlyMuffin on 2007-09-02
Your suggestions worked for everything except the directions. Up/Down/Left/Right are being handled by the analog stick, any clue why?

---

### Post by acoustibop on 2007-09-03
Is that a problem, DeadlyMuffin?  I have a Logitech RumblePad 2, and one of the nice things about it is that it has a mode button that enables me to swap functions between the directional pad and first analog stick.  That means I can use the analog stick as directional controller in digital-only situations; it's a much better way to control the direction than the pad.

Give it a try with the analog stick; you might like it.

---

### Post by Gasten on 2007-12-06
Hello. I have the same problem, but mapping buttons/axes to keyboard/mouse doesn't suffice (even if it's nice). Is there a way to - say- map one axis to another (ie map axis 3 ond 4 to 2 and 3, etc)?

Thanks.

---

### Post by landeel on 2008-04-20
[http://www.mediafire.com/?msitbdej0ad]("http://www.mediafire.com/?msitbdej0ad")
This is patched version of the **jscal** utility from the **joystick** package. It will allow the remapping of buttons and axes directly into the driver.
It's compiled for Ubuntu 7.10 AMD64, but you can recompile it to any version by doing a "**make clean;make**"

I have been looking for something like this for ages. Found it here: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=444142]("http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=444142")
I have many joypads / joysticks with many different button layouts, and by using this utility I can reconfigure the button layout by running a simple script, intead of reconfiguring every game and emulator everytime I want to use a different joystick.
Hope you find it useful.

---

### Post by deadlokIV on 2008-05-19
Oh my days, thank you so much landeel for the link to the patched source.
I've been spending around 2 days trying to find a cure to the illogical axis mapping the Xbox controller drivers have produced.

I thought that a more centralized joystick configuration interface would have existed by now? I think I'll try to give back to the community soon by at least *trying* to wrap a gui around this utility, once college backs off a bit.

Thanks, and good luck to everyone on their quest for *buntu goodness.

---

### Post by landeel on 2008-05-19
Yeah, I have considered creating a GUI around this, but didn't have the time to do it. Also, it would be extremely cool if the mapping profile would be loaded automatically when the device is plugged.
I think this patched JSCAL should go to the official repositories.
See, the linux joystick driver had the button/axis remapping API from the beginning, and there was absolutely no program on earth to take advantage of this feature. :)

---

### Post by brentmi Sato on 2008-05-28
I'm also having a problem with this.  I tried configuring all the buttons to one so I could figure out what code goes to what button, but all the codes are different.  The easy-fix for the config is what I had by default.  Everything works fine, just no down or right in Gens.  dgen is just too hard to figure out (and didn't work right when I could get it to work, not to mention configuring the joypad, which I couldn't even figure out how to do.  :/).

I tried installing qjoypad but it says I'm missing a dependency (libqt3c102-mt) and doesn't bother to help me find it.  I tried an apt-get and searching through the package manager and I got zilch.  I apparently already have the lib it was replaced with though, but it still won't allow the .deb to install.

Using Heron and a PS-to-PC adapter.  Works flawlessly for epsxe and zsnes.

I'm also noticing there's not a lot of choice when it comes to genesis emulators for Linux, and Gens is the only one with a GUI.  Kinda surprised.

[ETA]  If you're in that situation and are using a PS analog controller, hit the analog button then config it like you want to (i.e. not with the analog sticks)  I don't know why but that actually worked for me.

---

### Post by acoustibop on 2008-05-29
As far as GENS is concerned, brentmi Sato, megamaced has recently posted a [.deb for GENS]("http://ubuntuforums.org/showpost.php?p=4997623&postcount=329") with various improvements (including a patch that fixed the segmentation fault many people - myself included - were getting).

It's also the first version I've come across that configures the directional controls properly - in all previous versions I've had to configure these by editing the configuration file.

---

### Post by BeBoBli on 2008-06-20
No Joystick/Gamepad manager for Ubuntu?

---

### Post by arigram on 2008-06-20
How about **rejoystick** ?
[http://rejoystick.sourceforge.net/](http://rejoystick.sourceforge.net/)
It maps every joystick/joypad button to a keypress and saves configuration files that are run in the background when so desired. The only way to use my gamepad with a couple games in Wine.

---

### Post by landeel on 2009-06-24
I have found a way to load the button configuration automatically as soon as you plug the joystick. Thanks to udev. Check here: [http://ubuntuforums.org/showthread.php?t=761044&page=2]("http://ubuntuforums.org/showthread.php?t=761044&page=2")

---

