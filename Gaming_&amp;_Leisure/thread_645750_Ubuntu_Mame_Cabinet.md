---
title: "Ubuntu Mame Cabinet"
date: 2007-12-20
forum: Gaming &amp; Leisure
---

### Post by brpadington on 2007-12-20
I have been using ubuntu since version 5.10 and it is the only distro that works with my wifi card out of the box. Anyway i just purchased an arcade cabinet that i have installed a PC inside to use with emulators(mainly mame) I was wondering if any of you guys have done something similar with ubuntu.  Ideally i would like to set it up to automatically boot up into some sort of front end that would let me select which emulator(NES,snes etc) Any suggestions would greatly appreciated.

---

### Post by govee on 2007-12-21
Do a search for SDLmame as it is the most up to date arcade emulator for Ubuntu . As for Frontends there are a number to choose from. Kxmame, Wahcade, and a few more. I use SDLMame with Wahcade and I am also trying to figure out how to get the frontend loaded at startup. If you did emulation under windows I think you will find it pretty easy to do with linux, with a little more work though. I would imagine since you have been using Ubuntu for so long, that the extra work required, you will already understand and it will seem inconsequential.

---

### Post by disturbedite on 2007-12-21
yes, yes, yes.  what govee said.  use sdlmame definitely.  its the only mame variant that is still actively developed.
if you need a frontend/gui with sdlmame, i'd recommend kxmame.  (but *don't* install the kxmame package from the ubuntu repo, its too outdated & doesn't support sdlmame).
see my post here for info on getting an ubuntu package of sdlmame & compiling kxmame:
[http://ubuntuforums.org/showpost.php?p=3965888&postcount=5](http://ubuntuforums.org/showpost.php?p=3965888&postcount=5)

---

### Post by brpadington on 2007-12-26
Thanks a lot guys! I really appreciate the help. I stumbled on some how to's for sdl mame and they seem very well documented. Thanks for the warning on kxmame from the repos because i was getting ready to try that and it would have been frustrating. Wehn i  get everything up and running i'll post some pics.:guitar:

---

### Post by ijason on 2007-12-26
i may be a bit obtuse, but couldn't you just run the GUI program from the >System >Pref >Sessions? so that it starts every time ubuntu starts? then once you get past the log-in screen it will automatically start. and, if you run the emulator on a guest-user of ubuntu, you can just have it auto-login after 30 seconds.

---

### Post by ijason on 2007-12-26
i'm curious, how much did you buy the arcade cabinet for? i'm thinking there might be a decent business fabing arcade cabinets with 27" displays and the cushy arcade buttons/sticks running to a usb controller. then all the buyer does is build a PC and stick it in there and plug in the usb.

kinda a turn-key system for the arcade hardware.

---

### Post by brpadington on 2007-12-27
Mine is an old NEO-GEO cabinet. I didn't want to take a classic one and ruin it. I only paid 50 bucks and the cabinet was completely working when i bought it minus the display. The control panel had been recently refurbished with new sticks and buttons. I too have thought about building cabinets to sell but i have not convinced my wife yet haha.:popcorn:

---

### Post by nellistc on 2007-12-30
Hi,

I'm running xubuntu in a cocktail cab. GDM is configured to automatically login and wah!cade is set to autostart. I use a basic X session running Openbox. As others have mentioned, you can keep running xfce (or another desktop environment) and just run the frontend at startup.

I'd recommend you grab a copy of sysv-rc-conf and use it to disable all the services you don't need. This may improve boot times a little. My 2Ghz P4 takes around a minute from power-on to a loaded frontend.


cheers.

---

### Post by brpadington on 2008-01-02
Thanks for the tip. After fighting with Gutsy's wifi problems for 2 days i put xp on it and 1 hr later i had a fully working upright cabinet... I think i will eventually put feisty on it as that was the last release that worked flawlessly with my wifi.  By the way how didf you hook up your controls?? i tried soldering the buttons to some playstation gamepads but one of the pads stopped working a few days later... I just bought a Keywiz Max and put it in and i am loving it. Talk about a great product.  Anyone else used one?

---

### Post by nellistc on 2008-01-02
Hi,

I'm using an ipac, which is similar to the keywiz. The ipac2 has enough inputs for 2 joysticks, 6 buttons per player, a coin mech and P1/P2 start buttons. Sure beats soldering gamepads and/or keyboards :)

---

### Post by brpadington on 2008-01-03
Thats no joke i spend hours soldering those gamepads. I used to work at a plant that built PCB's so i have plenty of practice but it is still teadious as hell... I almost got an ipac but i saw the keywiz and thought i would try the underdog. From what i have heard both work really well.

---

### Post by koshari on 2008-02-24
rather than use a window manager at all why don't you just give the application its own gdm listing and boot it directly from the gdm login, 

you can set the auto login properties in gnome and set it to be the default session, and on exit pres cont/alt/backspace to get back to the gdm screen.

---

