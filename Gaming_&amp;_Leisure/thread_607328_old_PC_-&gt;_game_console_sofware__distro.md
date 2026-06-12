---
title: "old PC -&gt; game console sofware / distro?"
date: 2007-11-08
forum: Gaming &amp; Leisure
---

### Post by nihilocrat on 2007-11-08
Half of the reason why I'm asking this here is because I can't think of a good Google query that will find what I want. I have an old laptop (and desktop, not sure which to use) which I would like to repurpose as a console game emulator to connect to a TV with no keyboard or mouse necessary; basically a stand-in for a real console (I've been too poor in the past several years to afford consoles) that can play Playstation One games and anything older (including some DOS games via DOSbox). Of course, it would be an added bonus to play Linux-native games or perhaps even Wine games which would work.

The biggest piece of this would obviously be some sort of frontend that would come up after the system boots to access said emulators / games with only a USB gamepad or other similar controller.

The only thing that I've been able to find so far that sort of fits this bill is the LiveCD for AdvanceMAME, but it's too focused on MAME (I'd really rather be playing Genesis / SNES games most of the time) and it seems like it's intended to be run with a keyboard and mouse. I also checked out Entertainment PC distros / software like LinuxMCE and MythTV, but obviously those are oriented towards DVR and not emulators.

If I wanted to roll my own, I would probably use sometihng like Damn Small Linux as a base, a thoroughly stripped-down version of Ubuntu, or something in between. I'd write some sort of frontend in SDL and some GUI package for SDL (unless there is a way of navigating a window manager with a gamepad) to select game system (i.e. emulator) and the particular game to play. If I felt lazy, I wouldn't add any sort of configuration interface and instead just SSH in whenever I wanted to edit config files for the emulators.

So please, if you know of anything like this, enlighten me.

---

### Post by disturbedite on 2007-11-08
boy this sounds like an interesting idea....kinda like some mame boxes ppl make...
but i'm not aware of any software/distro for this purpose....
closest thing i could think of is mythtv, but thats not what you want to do...

---

### Post by wounded on 2007-11-09
mymediasystem.org

MMS is what I use and I abslutely LOVE it. It is sort of a mythtv type deal but I use it just for watching videos and playing games on my desktop computer hooked up to my tv. 

The current stable release is great for playing roms and native games on. I just use my keyboard most of the time but I sometimes have rejoystick running in the background set up so I can use my PS1 controller (That is hooked up to my comp) to navigate the menus. If you have a remote that works with your computer I tihnk you can set up lirc so you use the remote control to go through the menus and everything.

When installed via apt-get (With their repositories in your sources.lst) it installs an MMS session in GDM that you can log into so thats the only thing running. The games module can run bash scripts which means native games can run with rejoystick in the background (Which can be killed after) so you can play games that dont have joystick support with it, as well as set up dosbox profiles before hand and then just make a simple script to run those games. It isn't the perfect solution but it is definately one worth checking out.

---

### Post by MonkeyBoy on 2007-11-09
Interesting that you bring this up as I am in the process of doing something similar with an old laptop.  

Try having a google for ArcadeOS.  It is basically dos but designed to run on mame boxes.  

If you are keener on sticking with Ubuntu try Kamefu from the repos.  It is a frontend that can index and launch roms using various different emulators so you can have a list of all your mame, snes, genesis, etc roms all in the same place.

There is another app in the repos called joy2key (I think) which might be useful in configuring things so your pc boots to Kamefu and is then fully usable just with a gamepad.

Good luck with your plans.  

Sadly I think I need to use win98 as the base for my games console because of the badly supported old compaq hardware but it should still be good.

---

