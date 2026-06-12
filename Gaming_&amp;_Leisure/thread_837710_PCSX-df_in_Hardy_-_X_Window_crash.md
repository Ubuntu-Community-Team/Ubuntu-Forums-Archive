---
title: "PCSX-df in Hardy - X Window crash?"
date: 2008-06-22
forum: Gaming &amp; Leisure
---

### Post by Gespenst_MkII-M on 2008-06-22
Fair warning: I'm not a Linux expert by any means. I just switched over about four or five months ago, and mostly used Kubuntu 7.10 for 64-bit systems, only recently changing to a 32-bit distro. So if the info I provide below isn't enough, please tell me how to get more.

**System:** Kubuntu 8.04, 32-bit version (using a 64-bit AMD processor, however)

**Video card:** ATI Radeon 9800 Pro with the restricted drivers for it installed. Oddly, I find that the repositories do not have the commonly suggested "glxgears" program for testing how well things are running.

I'm using the pcsx-df package from the main repository, with various plugins downloaded from the same source.

Here's basically what happens when I load pcsx (did it from console this time to get a readout of the results):

User input in terminal: pcsx
Result: PCSX GUI loads, with terminal showing the following ('terminal output', etc. is my embellishment, not actual system output):

===Terminal output===
Checking plugin_is_available - libDFXVideo.so
Checking plugin_is_available - libDFSound.so
Checking plugin_is_available - libDFCdrom.so
Checking plugin_is_available - libDFInput.so
Checking plugin_is_available - libDFInput.so
DFInput warning: config file not found.
DFInput warning: config file not found.
Loading memory card /home/gespenst/.pcsx/memcards/card1.mcd
Loading memory card /home/gespenst/.pcsx/memcards/card2.mcd
===End output===

Next I went to Configuration -> Plugins & BIOS, getting this:
Result: Plugin configuration screen shows up as expected. Terminal output as follows:

===Terminal output===
Scanning /usr/lib/games/psemu/ for plugins
    Plugin file symlink: /usr/lib/games/psemu/libDFSound.so -> /home/gespenst/.pcsx/plugins/libDFSound.so
    Plugin file symlink: /usr/lib/games/psemu/libDFCdrom.so -> /home/gespenst/.pcsx/plugins/libDFCdrom.so
    Plugin file symlink: /usr/lib/games/psemu/cfgDFIso -> /home/gespenst/.pcsx/plugins/cfgDFIso
    Config file symlink: /usr/lib/games/psemu/cfgDFIso -> /home/gespenst/.pcsx/plugins/cfg/cfgDFIso
    Plugin file symlink: /usr/lib/games/psemu/libDFInput.so -> /home/gespenst/.pcsx/plugins/libDFInput.so
    Plugin file symlink: /usr/lib/games/psemu/cfgDFXVideo -> /home/gespenst/.pcsx/plugins/cfgDFXVideo
    Config file symlink: /usr/lib/games/psemu/cfgDFXVideo -> /home/gespenst/.pcsx/plugins/cfg/cfgDFXVideo
    Plugin file symlink: /usr/lib/games/psemu/cfgDFSound -> /home/gespenst/.pcsx/plugins/cfgDFSound
    Config file symlink: /usr/lib/games/psemu/cfgDFSound -> /home/gespenst/.pcsx/plugins/cfg/cfgDFSound
    Plugin file symlink: /usr/lib/games/psemu/cfgDFCdrom -> /home/gespenst/.pcsx/plugins/cfgDFCdrom
    Config file symlink: /usr/lib/games/psemu/cfgDFCdrom -> /home/gespenst/.pcsx/plugins/cfg/cfgDFCdrom
    Plugin file symlink: /usr/lib/games/psemu/cfgDFInput -> /home/gespenst/.pcsx/plugins/cfgDFInput
    Config file symlink: /usr/lib/games/psemu/cfgDFInput -> /home/gespenst/.pcsx/plugins/cfg/cfgDFInput
    Plugin file symlink: /usr/lib/games/psemu/libDFIso.so -> /home/gespenst/.pcsx/plugins/libDFIso.so
    Plugin file symlink: /usr/lib/games/psemu/libDFXVideo.so -> /home/gespenst/.pcsx/plugins/libDFXVideo.so
Could not open plugins directory: '/usr/local/lib/games/psemu/'
Could not open plugins directory: ''
Scanning bios dir /home/gespenst/.pcsx/bios
  Checking is_valid_bios_file - /home/gespenst/.pcsx/bios/..
  Checking is_valid_bios_file - /home/gespenst/.pcsx/bios/.
  Checking is_valid_bios_file - /home/gespenst/.pcsx/bios/SCPH1001.BIN
    /home/gespenst/.pcsx/bios/SCPH1001.BIN is a valid BIOS file
Finished scanning bios dir /home/gespenst/.pcsx/bios

(<unknown>:31978): Gtk-CRITICAL **: gtk_file_system_unix_get_info: assertion `g_path_is_absolute (filename)' failed
BIOS directory is now /home/gespenst/.pcsx/bios
Scanning bios dir /home/gespenst/.pcsx/bios
  Checking is_valid_bios_file - /home/gespenst/.pcsx/bios/..
  Checking is_valid_bios_file - /home/gespenst/.pcsx/bios/.
  Checking is_valid_bios_file - /home/gespenst/.pcsx/bios/SCPH1001.BIN
    /home/gespenst/.pcsx/bios/SCPH1001.BIN is a valid BIOS file
Finished scanning bios dir /home/gespenst/.pcsx/bios

(<unknown>:31978): Gtk-WARNING **: file_system_unix=0x834c800 still has handle=0x82bc030 at finalization which is NOT CANCELLED!
DFInput warning: config file not found.
DFInput warning: config file not found.
===End output===

Well, everything I understand sounds okay. So I go to File, Run CD (or Run CD through BIOS, both have similar results), and...

Result: PCSX window immediately vanishes and the program is removed from memory; it has apparently crashed.

===Terminal Output===
Checking plugin_is_available - libDFXVideo.so
Checking plugin_is_available - libDFSound.so
Checking plugin_is_available - libDFCdrom.so
Checking plugin_is_available - libDFInput.so
Checking plugin_is_available - libDFInput.so
DFInput warning: config file not found.
DFInput warning: config file not found.
The program '<unknown>' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 11 error_code 8 request_code 140 minor_code 14)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
===End output===

That's where the crash occurs. This happens regardless of whether I try to load a game from CD (my drive works fine, I'm certain of this) or from an image-file (the image files are valid, I'm also sure of that). My BIOS is also good, I know that since it's the same file I was using for my Playstation 1 emulator in Windows 2000.


Just in case it matters, the two games I've been trying with this are Super Robot Taisen F and F Final (both Japanese games, imported; both run near identical code/engine/etc.). 


**Other possibly useful info:** I'm relatively sure I have 3D acceleration going. Sort of. I can play first person shooters and such, though the framerates are nowhere near as good as they were back on Win2000. Once I installed 32-bit Hardy, I also installed the proprietary drivers and I assumed that was all I needed.

Notably, when I try to run pSX (another emulator) on here, through an old 7.10 debian package made by dfreer, it... works. Sort of. SRT F and F Final both load just fine, but they're *really choppy.* Sound is choppy, video is choppy, etc. I dread what would happen on something using real 3D graphics, like Final Fantasy 7. I can't seem to find Hardy-specific packages of it on his repository, in any event.

Also, mupen64 (an N64 emulator) exhibits similar problems; it's really, really slow. Granted, the only game I tried with it was Super Robot Taisen 64 (Yes, there's a trend here). I'm certain it's not how these games are programmed... again, they all worked really well on my relevant windows emulators.

If I need to supply more info, please let me know how to get it. I fully admit I'm still very new to Linux, and I won't freak out if the above isn't enough to troubleshoot it.

---

### Post by FranMichaels on 2008-06-22
I've had it happen twice. I'm at a loss as well. I've set it to use xvideo rather than opengl, works smoothly. The run cd vs run cd through bios, is because pcsx actually has it's own internal bios it can use instead of requiring the sony one. It's pretty cool. I played through symphony of the night with no problems (I'm especially please because I backed it up from my disc which is quite scratched...)

It's some sort of bug for sure though, if its effecting different hardware. Mine is an intel i945gm (laptop on board video). Also, just type 

glxgears

at the prompt, it should do what you expect :)

As for n64, try [mupen64plus]("http://code.google.com/p/mupen64plus/"), runs nicely with the rice video opengl plugin for me. No X crashes with it either...

---

### Post by FranMichaels on 2008-06-22
Hmm, actually my issue is solved. Take a look at your 
Xorg.0.log.old after an X crash

less /var/log/Xorg.0.log.old

Based on the error I found this
[https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/220019](https://bugs.launchpad.net/ubuntu/+source/xorg/+bug/220019)

And an update for the intel driver. So perhaps it's a driver issue and not an PCSX-df at fault. Do you ever have an X restart when loading a Video file or anything?

---

### Post by Gespenst_MkII-M on 2008-06-22
Thanks for the quick reply! I'll try to go over the things you've brought up.

**Edit 3:** Found glxgears. Wasn't part of its own package, but rather part of mesa-utils, as I found out after some more research. Chalk up a Moron Point for me.

My glxgears benchmarks are generally like: 
8318 frames in 5.0 seconds = 1661.014 FPS
(Minor fluctuation within that value)

But here's something interesting! When I close glxgears, I get this in my terminal: XIO:  fatal IO error 11 (Resource temporarily unavailable) on X server ":0.0"
      after 156744 requests (152664 known processed) with 0 events remaining.
Segmentation fault


On mupen64plus: My mistake, I should have specified; I am indeed running mupen64plus, obtained from their Google Code page. Version 1.4 for 32 bit, I believe. It, much like pSX, is really slow. I'd say the framerates are in the 3 to 10 FPS range. Of course, FPS games behave similarly the moment I come across more than one or two opposing players online in things like Tremulous, etc., so I'm not sure this is a software issue.

On the x.org logfile: I'm looking at it, but I only understand the theory of what I'm seeing here. I cannot make realistic use of this information. What am I supposed to do with this? Post the contents for review? (It's a LOT of text, that seems like an unwieldy solution)

**EDIT:** Aha! I see what you mean now, now that I've researched this in conjunction with the topic below. No, this isn't quite my problem. What happens is PCSX just goes 'poof', vanishing... but I can continue to use the rest of my OS normally. I can even re-load PCSX, though it will once again crash if I try to play anything.


On X restarts when loading video files: You mean like having something crash or reload when I, say, watch an .avi, .mkv, .rm, .mpg, etc. file? Not to my knowledge. If there is a crash or restart, it's invisible to me. Most of the time, Kaffeine (or another video player; sometimes I have to use other ones to get some formats to work right) loads up just fine and plays the video at mostly full speed.


Summary: I seem to catch signal 11 crashes, just not in the same ways you're expecting/experiencing? Hm.

---

### Post by FranMichaels on 2008-06-22
I see, it was actually just a guess, hoping you could find something that would help you find/make a bug report. 

My guess is it is the restricted driver though, have you tried the open source driver for your card? It could just be that 2d acceleration is poor for the proprietary driver, or something about it just makes pcsx-df fail.

Sorry I can't be more helpful...

If glxgears gives you a reasonable rate 1000ish fps with the open driver, I'd say stick with it and see if the problems are solved. At least with that someone other than Ati/AMD can fix a driver bug...

---

### Post by Gespenst_MkII-M on 2008-06-22
That's alright. Thank you for your help all the same. I'll wait and see what comes up from future releases, since this isn't critical.

---

### Post by acoustibop on 2008-06-23
What's your output for fglrxinfo, Gespenst_MkII-M?  glxgears has been installed on all the Ubuntu systems I've run by default.  It comes as part of the mesa-utils package.  You can also try fgl_glxgears if you have the fglrx driver installed.

I have to say I'm running an ATI 9800 XT on a 32bit Hardy systen, and pSX Emulator (and PCSX) run perfectly well; pSX, my Playstation emulator of choice, has run perfectly on every Ubuntu release since Edgy, with a couple of other videocards too, a 9700 Pro and a 9800 Pro.

Mupen64 runs well for me bit with a few glitches - this is probably because I haven't bothered to configure it much past setting up my controller.

---

### Post by Gespenst_MkII-M on 2008-06-23
...That's a really, really good question. I wasn't aware there was such a program. But when I read it, here's what my terminal showed (includes my own input):

===
gespenst@gespenst-desktop:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: DRI R300 Project
OpenGL renderer string: Mesa DRI R300 20060815 AGP 8x x86/MMX+/3DNow!+/SSE2 TCL
OpenGL version string: 1.3 Mesa 7.0.3-rc2

Segmentation fault
gespenst@gespenst-desktop:~$
===

Something tells me I shouldn't be seeing those outputs... does it matter that my card was made by Rosewill? ATI Radeon 9800 drivers have always worked for it and as far as I know it is a Radeon 9800 in every way besides who built it.

Interesting all the same. Thanks for telling me about fglrxinfo.

**Edit:** Also, for what it's worth... I'm more than willing to go with alternative solutions. PCSX isn't my obsessive end-goal. If something else comes up such that "Oh! If you do X and run Y instead, you'll get full-speed emulation of (system)", I'll go for that.

---

### Post by acoustibop on 2008-06-23
That means your fglrx driver isn't properly installed, Gespenst_MkII-M.  As an example, I get```
fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9800 XT
OpenGL version string: 2.1.7412 Release
```
If the driver is properly installed, you should get the ATI OpenGL details, not the Mesa one.

You could also try glxinfo; it prints out quite a lot of stuff, but the first few lines are the ones that matter; particularly you should get the 'direct rendering: Yes' line.```
glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
```Otherwise DRI isn't enabled.  How did you install the fglrx driver?

---

### Post by Gespenst_MkII-M on 2008-06-23
(Feel free to just call me "Gespenst" for short; that can't be fun typing the whole thing out?)

Well! There's my problem, huh? Or part of it at least; I ran glxinfo and it doesn't give the short, pretty "All is well" output you got. Mine was a long batch of hardware addresses, and most importantly this line: "Direct Rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)"

So you're right, there seems to be an issue with how I installed the drivers. As for how I did it? When I first booted Kubuntu 8.04 (32 bit), a small icon looking vaguely like a PCI board appeared in the bottom right corner of my task bar, near the Klipboard (Klipper?) and clock and so on. I clicked it, it asked me for my password, and it showed a single entry; ATI accelerated graphics driver (may not be the exact term, I am doing this from memory). I told it to Enable those, it got them via apt-get or a similar method, and that was the last I bothered with it.

...And here's something interesting. When I went to K -> System -> Hardware Drivers Manager, and my ATI Drivers entry is now **unchecked.** I have run various Adept-retrieved system updates since the time I did the driver installation, of course (this copy of the OS has been running for about two weeks now, I think). Among them, I did pick up mesa-utils so I had glxgears and such.

Part of me is tempted to say "Oh, easy fix. Just click to enable the ATI drivers in Hardware Drivers Manager and see if it 'sticks' this time." The other part of me says "No, wait, let those with a bit more knowledge weigh in on that first." -- I'm listening to said other part for now.

---

### Post by acoustibop on 2008-06-23
Well, I installed the fglrx driver through Hardware Drivers (probably the small PCI logo you saw) and it was that easy, Gespenst - doesn't really matter if I use the full name or not, actually; I usually post usernames by copy + pasting them.  I think it's rude to misspell people's names, and that helps to make sure you get them right. ;)

The version of the fglrx driver that's installed in Ubuntu (probably the same as in Kubuntu) is AIR 8.3, which is quite recent; only about 2 or 3 months old, I think.

A couple of things I always do when I've installed the fglrx driver (don't do them 'till you've rebooted) are first
```
sudo aticonfig --initial -f
```
and then
```
sudo aticonfig --overlay-type=Xv
```
The first sets up the configuration file for the fglrx driver and the second sets the overlay method to be used.  I don't think it's likely, but possibly if you don't set up the configuration, maybe the driver doesn't stick?  Whatever...

If you do continue having problems with the fglrx driver, I'd recommend the [Unofficial Wiki for the ATI Linux Driver]("http://wiki.cchtml.com/index.php/Main_Page") - as well as being an excellent source of howtos for installing the driver, it's also an excellent troubleshooting resource.  Until Ubuntu made installing a recent driver so easy through Hardware Drivers, I always used to use the current Unofficial Wiki for the ATI Linux Driver method.

---

### Post by Gespenst_MkII-M on 2008-06-23
**Yay!** Or as Captain Falcon might say, "Yehs!" While PCSX still crashes, I've stopped caring; pSX mostly works. It's about 90% speed with only minor sound skips, which is enough to play SRT games. The only problem I have now is I can't seem to create memory cards in pSX, but I think I fixed that by making them in PCSX and copy/pasting. Woo.

mupen64plus is also running at high enough speed for the games I want to be playable, and I think I just have to fiddle with its configuration to make it play nice with my gamepad, which I'm about 85% confident I know how to do or can figure out on my own.

I'm astounded. Something, somehow, disabled the ATI drivers. Re-enabling them fixed most of my issues. PCSX may not be working, but I really don't care at this point. Issue Resolved as far as I'm concerned, and thank you for the info!

---

### Post by acoustibop on 2008-06-23
Yes, the plugin-based Playstation emulators are not in the least user friendly, Gespenst - and part of that is the difficulty of selecting the right plugins and configuring them.  Air the *only* video plugin I could get working more or less correctly in those emulators was Pete's OGL2 one, and that one still required all sorts of finicky configuration, including changes for different games.  Apart from the fact that it works better anyway, pSX is *so* much easier (aspirin-free as well!)...

How are you trying to create memory cards in pSX?  The right way is to go to the Memory cards screen, Eject a slot, click the browse (...) button, navigate to where you want to create the card, type its name in the Selection: panel at the bottom (extension doesn't matter.  pSX doesn't care, and I don't bother), and click OK and OK.

Having created the card, you may need to format it.  Most games will format the card automatically on first use, but not all - run pSX with your card loaded, but without loading a game, so the emulator runs to the BIOS screens (where you can select the memory card editor and the CD player).  Open the memory card editor (you'll need your controller set to Normal type for this.  Dualshock won't work, just as with a real Playstation).  Once it opens, it'll format the card (you won't see anything), so just close it again and restart with a game.

This works infallibly for me.  AFAIK about the only thing that can go wrong is if you're trying to create the cards somewhere where you don't have the appropriate permissions.  So your Home folder is a good place; AIR the default location for pSX is ~/.pSX/cards - so that should be fine.

What sort of machine are you running on?  And do you have any other applications running when you're playing games?

---

### Post by Gespenst_MkII-M on 2008-06-23
Ah. I was close. I saw where I could **pick** a card, but I didn't think that'd let me make one. I ended up just having PCSX make a pair for me and copying them over, which worked fine (Super Robot Taisen F complained about it not being formatted, then took care of it, much like you'd expect). So that wasn't a case of read/write permissions, so much as "...I can make one from there? Huh." - User didn't know about that.

I have other programs running, but nothing memory intensive. A few text files (in Kate), Firefox (with only a few simple pages open, no Flash stuff like Youtube) and so on when I play. No big deal. pSX is working swell now, mupen64plus is mostly working (and I'm confident I can figure out the controller issue on my own, that's got to just be a case of editing a config file or something...), and I bet first person shooters will run better now too. Seriously; it's orders of magnitude better.

Turns out something did indeed just uninstall the ATI drivers and I had no idea when I made the original post. Not sure what or how, but it did. Reinstalling them worked fine and everything's mostly playable; the parts that aren't, I know I can handle alone.

So... yeah, while PCSX is crashing, I no longer really care. pSX is working just fine and I am now having fun making old 1980s anime giant robots shoot one another. 'Issue resolved' as far as I'm concerned. Thanks again for your help.

---

