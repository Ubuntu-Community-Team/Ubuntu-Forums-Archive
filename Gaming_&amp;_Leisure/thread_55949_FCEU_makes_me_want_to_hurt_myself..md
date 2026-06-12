---
title: "FCEU makes me want to hurt myself."
date: 2005-08-10
forum: Gaming &amp; Leisure
---

### Post by Dragular on 2005-08-10
Ok.  I downloaded the .deb package for FCEU.  After bashing my head against the keyboard enough times, I slipped up on dpkg, and installed FCEU.  Everything went well!

now, when I want to use FCEU, I have to go to /usr/games/ and click fceu.  Only that does absolutely nothing.  Then when I try going in a root terminal to /usr/games/ and TYPING fceu, i get "Command not recognized"

Please, for the love of God, all I want is to play my freaking Roms.

---

### Post by BoyOfDestiny on 2005-08-10
I hear ya, using FCEU under linux is more of a pain in the butt than under windows. Make sure you install FCEU from synaptic (you need the universe repostory enabled).

What I do as a workaround is right click on one of ur roms, and choose open with (or whatever it is) and put fceu as the command. That will load your game.

RANT:
Now the real fun begins, the default keyboard layout for FCEU in linux is dumb. Why do I say dumb? it uses the numeric keypad. I have a laptop... my laptop doesn't have one... I have to press a "func" key, but then u can't use the A and B buttons... Last on my rants is, you could just go and edit the config file right? Wrong, it's a binary...

CONCLUSION:
Anyway bottom line,
nintencer is a step in the right direction [http://nintencer.fobby.net/](http://nintencer.fobby.net/)
It's easier to config the keyboard, gamepad, etc, and is based on FCEU (since as far as I know it's now abandoned)

I need something for NES like ZSNES for SNES (Which is always great regardless of windows or linux).

---

### Post by Dragular on 2005-08-10
[QUOTE=BoyOfDestiny]Make sure you install FCEU from synaptic (you need the universe repostory enabled).[/QUOTE]

How would I go about doing this?  The box I've put Ubuntu on isn't connected to the net (figured I better keep my test subject away from the network until I know what I'm doing lol), so I've been transferring my .deb files via floppy or cd-rom... how can I use synaptic to do that?  I tried, but the only option I could really find was to find a repository... and i got lost at that point lol.

---

### Post by BoyOfDestiny on 2005-08-10
Just go ahead and put it on the net, ubuntu doesn't need a firewall etc. 

I guess it's easier to use synaptic, you don't really have to. 

I'm not sure how synaptic handles adding repositories, so I do a quick 
sudo gedit /etc/apt/sources.list

just uncomment the lines (remove the #) next to the ones with universe in it.

To be honest I'm still somewhat a newbie but since you said typing fceu didn't do anything, I figured it wasn't installed "globally" for lack of a better term. When I installed with synaptic I could run fceu from any dir... 
Anyway good luck.

---

### Post by Mishura on 2005-08-11
If you have a gamepad that works in Linux (My recommendation:  PSX or PS2 controller with USB adapter--$10 at RadioShack) then you can use QJoyPad (Look for it at KDE-Apps.org) to map the keyboard controls to your gamepad.   Using this makes playing NES games with FCE Ultra *Much* better.  If you don't have a gamepad.. then remapping the buttons, if its possible, is going to be hell.

Why oh why nobody made a frontend to FCEU, I'll never figure out.

---

### Post by BoyOfDestiny on 2005-08-11
I have the same adapters from radioshack myself =), 
Yikes, it works by default already! You don't need to use anything, it's just u have to configure fceu to use a gamepad via commandline. 

You're essentially using a hack (since FCEU under linux is missing the gui of it's win counterpart). 

What I wonder is how this "emulation of keystrokes" works. As far as I know most keyboards cannot take more than 3 keys pressed at a time. That would totally stink for snes/some arcade games...

EDIT: I googled for an old post on it and here you go

fceu -inputcfg gamepad1 therom.nes

I think after you do this once, it keeps the settings.

---

### Post by Mishura on 2005-08-13
> fceu -inputcfg gamepad1 therom.nes

Interesting.  I should try that.  The QJoypad hack is a hack :) , but It does allow me to mod my gamepad to use the buttons to make it all seem like a NES controller (Start = Start, Select = Select.. down the line..).  One think I like about the program, is that I can have separate profiles for a lot of my games.  When I play Armagetron, I can use it to map my gamepad so that I don't have to use keyboard, and so on.  Especially with games like Vegastrike, where the options to map the joystick aren't clear, or games like XGalaga that don't have joystick support period.

---

### Post by dtfinch on 2005-08-13
I've found that FCEU runs very well on WINE. You get a full GUI. The only problems are that fast forward isn't very fast with sound enabled, and if I have anything running in the background, I need to renice FCEU and the increase the sound buffer size or it skips. I haven't tried Nintencer yet. Didn't know about it.

---

### Post by Mishura on 2005-08-14
[QUOTE=dtfinch]I've found that FCEU runs very well on WINE. You get a full GUI. The only problems are that fast forward isn't very fast with sound enabled, and if I have anything running in the background, I need to renice FCEU and the increase the sound buffer size or it skips. I haven't tried Nintencer yet. Didn't know about it.[/QUOTE]

Thats interesting, (And I'll have to give it a try--always looking to see what actually *works* in Wine ;) ).  However, I feel that if there's a native Linux version to a program, running the Win version under Wine seems kinda.. wrong?  (Not blasphemous, just not right.. for us.)  There are exceptions:  Heretic II Linux doesn't work in Ubuntu/Hoary--due to GlibC issues.  Heretic II Win does work via Cedega and Wine.  Sad, no?

In my spare time, I've been hacking together a simple Kommander-based Frontend to FCEU.  I'd like it to feature a lot of stuff, but right now, all it is is a Rom selector, with a Play button.. with a predetermined settings (800x600, fullscreen, opengl, scaled..).  Not really ready for prime time, and Not a exercise in GUI innovation.. but it works.. for me.  Maybe later I'll finish it to do something more, once I figure out the advanced features of Kommander Editor*.

[SIZE=1]* I'm not a programmer, I'm a scripter.. and a bad one at that.  Hence, why its not written in C++ or something.[/SIZE]

---

### Post by punkrockguy318 on 2006-06-12
[QUOTE=Dragular]Ok.  I downloaded the .deb package for FCEU.  After bashing my head against the keyboard enough times, I slipped up on dpkg, and installed FCEU.  Everything went well!

now, when I want to use FCEU, I have to go to /usr/games/ and click fceu.  Only that does absolutely nothing.  Then when I try going in a root terminal to /usr/games/ and TYPING fceu, i get "Command not recognized"

Please, for the love of God, all I want is to play my freaking Roms.[/QUOTE]

You don't need to hurt yourself anymore, my friend: [http://ubuntuforums.org/showthread.php?t=195413](http://ubuntuforums.org/showthread.php?t=195413)

---

