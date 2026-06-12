---
title: "Mupen64Plus v1.4 is now here!"
date: 2008-06-15
forum: Gaming &amp; Leisure
---

### Post by argor on 2008-06-15
[ from Richard42]("http://www.emutalk.net/showthread.php?t=44669")

Mupen64Plus v1.4 is now here!
We could have waited even longer and packed even more features into the new Mupen64Plus v1.4 release, but I thought that it was time to get another one out the door for people to play. There are some big new features, and major contributions were written for this release by: slougi, DarkJezter, ebenblues, Tillin9, Richard42, nmn, and okaygo. A summary of the changes:

Major New Features

    * Graphical debugger for R4300 core (build with 'make DBG=1')
    * On Screen Display
    * KDE4 GUI (experimental, compile from source)
    * Cheat system with Gameshark codes


Minor New Features

    * Single frame advance
    * Emulator playback speed up or down in 5% increments
    * Rumble Pak support with force feedback
    * Map emulator functions (fullscreen, stop emulation, etc) to joystick buttons or axis movements.
    * Volume up/down
    * Blight Input: Individually configure each direction of X and Y axis, which allows inverting the axis
    * JTTL_Audio: libsamplerate support for high quality audio resampling
    * GTK GUI: Search/filter box
    * GTK GUI: Accelerator keys
    * GTK GUI: numerous small changes and fixes
    * Overhaul of rom handling functions; numerous small fixes


Bug fixes

    * NoMemoryExpansion parameter to emulate 4MB console; fixes some games
    * Removed NoAudioDelay core option to resolve issue #48
    * Fix unresponsive emulator when game gets stuck in loop
    * GTK GUI: #6 - if a ROM is selected in the ROM browser and 'play' is pressed, emulation will start
    * GTK GUI: #62 - ROM browser column sorting works
    * Rice Video: Support hi-res textures with different scale factors for X and Y
    * Blight Input: don't use 100% CPU in configuration dialog


Mupen64Plus has a [Home Page]("http://code.google.com/p/mupen64plus/") over at Google Code, with lots of useful information, screenshots, a bug tracker, a discussion forum, etc.

To download Mupen64Plus v1.4, just grab the package that you want:
[URL="http://mupen64plus.googlecode.com/files/Mupen64Plus-1-4-bin-32.zip"]
Mupen64Plus-1-4-bin-32.zip[/URL]
[Mupen64Plus-1-4-bin-64.zip]("http://mupen64plus.googlecode.com/files/Mupen64Plus-1-4-bin-64.zip")
[Mupen64Plus-1-4-src.zip]("http://mupen64plus.googlecode.com/files/Mupen64Plus-1-4-src.zip")

---

### Post by BigSilly on 2008-06-15
Mmmmmmmagic!!!

Thanks for the heads up here. I'm off to get it in!

---

### Post by acoustibop on 2008-06-15
Me too! :)

---

### Post by BigSilly on 2008-06-15
Quick play - loads of improvements, not least of a load of stuff that didn't work before now does! Won't go into too many details, but suffice to say this emu goes from strength to strength.

Congratulations to the Mupen64Plus team. Marvellous, marvellous work. 

:guitar:

---

### Post by grossaffe on 2008-06-15
seriously?  I just got 1.3 working last night!  I eventually broke down and downloaded the binary since the source-code wouldn't compile with a working RSP plugin.

edit:  Question, does this have support for the wiimote via cwiid or something?  also, can you save multiple controller profiles so you can have a different profile for different games or something of the like?

---

### Post by BigSilly on 2008-06-15
I only ever use the binary, so I dunno about compiling it.

I reckon you'd be better off asking them at the EmuTalk forums [here.]("http://www.emutalk.net/forumdisplay.php?f=113") They'll know more, since it's the home of the development team.

---

### Post by grossaffe on 2008-06-15
> **BigSilly said:**
> I only ever use the binary, so I dunno about compiling it.

I reckon you'd be better off asking them at the EmuTalk forums [here.]("http://www.emutalk.net/forumdisplay.php?f=113") They'll know more, since it's the home of the development team.

ugh, i don't think i can handle joining another forum.  I've recently joined like... three more in the past month. My feeble heart can't handle another forum.

---

### Post by BigSilly on 2008-06-15
> **grossaffe said:**
> ugh, i don't think i can handle joining another forum.  I've recently joined like... three more in the past month. My feeble heart can't handle another forum.

Oh go on! Nothing gets done unless someone says something! :D :D

---

### Post by grossaffe on 2008-06-15
> **BigSilly said:**
> Oh go on! Nothing gets done unless someone says something! :D :D

Alright, i'll think about it, but i'm not doing it today.  I'm still up from yesterday's nightmare of getting my wiimote to work with my computer.  I finally got it working under windows (Unfortunately, GlovePIE blows linux programs out of the water at the moment).  and then, of course, I finally got Mupen64Plus 1.**3** working last night :mad:.  maybe i'll give 'em my two cents tomorrow.

edit, and seeing as how you're in England, its 1 PM here on the east cost of America, and i've been awake for about 24 hours now (kind of sad, actually)

---

### Post by BigSilly on 2008-06-15
> **grossaffe said:**
> 
edit, and seeing as how you're in England, its 1 PM here on the east cost of America, and i've been awake for about 24 hours now (kind of sad, actually)

Bloody hell dude. It's only 6:15pm here in the Yook. Time to turn off your PC and get some kip matey. :) Hope you manage to get some in. :)

---

### Post by Naegling23 on 2008-06-16
excellent, ill try this out when I get home today.

Does gauntlet legends work now?

---

### Post by BigSilly on 2008-06-16
Dunno. I don't have that one, but Shadow Man and the Turok games do!

So far so good, but anyone else noticing more slowdown than the last version? Couple of problems too with certain games causing a ucode crc error, which only closing Mupen seems to fix. I've never seen that before, so can only assume it's something unique to this new Mupen. I tried to use KI v1.2, but got the error shown in the picture I've attached. It worked in the last Mupenplus, albeit slowly.

Also, anyone got their rumble working with this? I have a rumble pad but not getting the rumble, even though I've set it in the pad config.

---

### Post by acoustibop on 2008-06-16
Erm, you won't get rumble in Linux, BigSilly.  There aren't really any drivers for it.  Someone posted here a few months back, though, pointing to [this thread]("http://www.emutalk.net/showthread.php?t=41977") on the Mupen64 section at emutalk.  The patch is for version 0.0.10 of Blight's input plugin, which is the version included with the new Mupen64Plus release.

---

### Post by BigSilly on 2008-06-16
> **acoustibop said:**
> Erm, you won't get rumble in Linux, BigSilly.  There aren't really any drivers for it.  Someone posted here a few months back, though, pointing to [this thread]("http://www.emutalk.net/showthread.php?t=41977") on the Mupen64 section at emutalk.  The patch is for version 0.0.10 of Blight's input plugin, which is the version included with the new Mupen64Plus release.

Sorry, but I'm a bit confused. The new release lists it's improvements, and one of those items is a rumble feature. I have a rumble pad and presumed it'd be compatible. If I've missed a trick please let me know, but it does state on the pad config screen that you can enable rumble. If there are no drivers for it, why did they incorporate it? :confused:

Anyone else having the same issues as me otherwise? I'm finding a lot of my games are just crashing...:(

---

### Post by acoustibop on 2008-06-16
Well, the idea is that the patch acts as a rumble driver, BigSilly.  I hadn't noticed that it said that in the release notes - however, my controller configuration doesn't give a rumble pak option (AIR from using this plugin in Windows, you can either have a memory pak or a rumble pak).

Ahem!  Looks like I'm still on version 1.3 of the emulator...

---

### Post by BigSilly on 2008-06-16
> **acoustibop said:**
> 
Ahem!  Looks like I'm still on version 1.3 of the emulator...

Hehehehe! Thought I was going crackers for a mo. Let me know how you get on with it. Sadly, I'm experiencing a number of crashes and bugouts that I haven't seen before in the older Mupen64Plus, so it's either me doing something wrong, or there's a couple of issues they've not ironed out fully.

According to the EmuTalk forum there's a kernel module you can apply that enables the rumble feature they now have in Mupen. I've not had a go yet, but I will look into it for sure. I'll be well impressed if I can get rumble going in Linux!

---

### Post by acoustibop on 2008-06-16
I had an older copy of Mupen64Plus installed that I'd forgotten about, and even when I directed my launcher to the new version, the old configurations were still hijacking the plugins.  Still, fixed that...

Yes, I'm finding the input plugin rather buggy (I have to say I'm not that worried about rumble).  Some of the buttons, although I can set them in configuration, and confirm that the new settings are there in the configuration file, don't seem to be working in games. :(

---

### Post by BigSilly on 2008-06-17
> **acoustibop said:**
> 
Yes, I'm finding the input plugin rather buggy (I have to say I'm not that worried about rumble).  Some of the buttons, although I can set them in configuration, and confirm that the new settings are there in the configuration file, don't seem to be working in games. :(

Ah. Now I think I'm having that issue too. I thought it was me going a bit daft, but I have noticed that I'm setting the pad, but then it doesn't work as it should in game. I'll keep trying it, and if it continues I'll let them know on their forums. Cheers for that.

---

### Post by acoustibop on 2008-06-17
Controls seem to be working properly now.  Doesn't seem as if rumble is working, although the option now appears on the plugin configuration.

---

### Post by Steveway on 2008-06-17
For rumble your Gamepad needs to support Force-Feedback and while many Gamepads have the motors etc, there aren't many specialised drivers with Force-Feedback. So while my Gamepad could, it can't because no one wrote a driver for Linux, it works like a Generic Gamepad without Force-Feedback.
Also there was a command or program that showed you if your Gamepad supports FF but I forgot what it was called.
Oh, yes, also. Gogogogo Mupen guys, you rock!

---

### Post by BigSilly on 2008-06-17
[Apparently, there is a rumble driver for Linux.]("http://code.google.com/p/mupen64plus/wiki/RumbleSupport") Not tried it myself yet, but the Mupen team say this works. If anyone here has some success with this, please let us know how you get on.

The Mupen team are indeed doing a top job. It looks like they're addressing the bugs over on the EmuTalk forums, so a big thanks to them for that, and I hope they continue to make one of the best Linux emus there is. I'm only sorry I'm no programmer and can't help in that capacity. I would at a heartbeat if I could. Nevertheless, well done guys.

:guitar:

---

### Post by braveerudite on 2008-06-25
Isn't more easy for someone to just compile a version for Ubuntu 32 and 64 version?  Isn't that why they provide the source code so then someone compile an RPM or.Deb file for their Linux distribution of choice?  You would do a great thing for the Ubuntu old school gaming community.

---

