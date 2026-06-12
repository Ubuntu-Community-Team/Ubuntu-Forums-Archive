---
title: "Gens/GS Milestone 5"
date: 2008-10-26
forum: Gaming &amp; Leisure
---

### Post by GerbilSoft on 2008-10-26
Here's the Milestone 6 release of my version of Gens, Gens/GS. Milestone 6 introduces the new MDP plugin system. Currently, plugins must be built into the Gens executable, but the next version will add support for external plugins.

Also, Gens/GS m6 has several new renderers: Scale3x, Scale4x, hq3x, and hq4x.

Downloads:
[LIST]
[*][Ubuntu 8.04+ (32-bit) package]("http://info.sonicretro.org/images/5/56/Gens_2.15.5-gs-m6-1_i386.deb")
[*][Source Code]("http://info.sonicretro.org/images/9/92/Gens-2.15.5-gs-m6.tar.gz")
[/LIST]

For more information, see [http://info.sonicretro.org/Gens/GS](http://info.sonicretro.org/Gens/GS)

---

### Post by megamaced on 2008-10-26
Very cool indeed. Its nice to have an identical version for Linux and Windows. I don't need to use Kega Fusion anymore :)

I'll link to Gens/GS in my Gens thread and let the Google spiders do their thing...

Keep up the good work!

And heres an RPM for anyone who needs it:

[http://www.zshare.net/download/50439696022b92a5/](http://www.zshare.net/download/50439696022b92a5/)

---

### Post by disturbedite on 2008-10-26
thanks so much guys!

and thank you megamaced! i came to this thread to see if anyone could make an rpm package.

UPDATE:
works great on opensuse 11.0 x86.

---

### Post by Disreali on 2008-10-26
:KSThanks for your efforts, Gerbil 

One question before I test it out. Will Gens/GS overwrite my existing Gens for Linux? I don't really care if it does, I was just hoping to try to run a side by side comparison.

---

### Post by megamaced on 2008-10-26
> **Disreali said:**
> :KSThanks for your efforts, Gerbil 

One question before I test it out. Will Gens/GS overwrite my existing Gens for Linux? I don't really care if it does, I was just hoping to try to run a side by side comparison.

Installing Gens/GS will remove Gens. There is no need to perform a side by side comparision, Gens/GS is far superior.

---

### Post by wingnux on 2008-10-26
Thank you VERY MUCH! =)

---

### Post by nerdy_girlscout on 2008-10-29
sonicretro seems to be down. :(

I am really looking forward to trying the emulator though!

EDIT: It went up again, and I have your Gens version installed! :D

You've taken an emulator I couldn't even stand before, and made it great! Thanks! And while I am on x86 (32-bit) myself, I still think that your decision on replacing the asm code is a good move for portability.

Now there's just one bug a saw. This isn't new though, it's been in the GNU/Linux port forever I think. Anyway, if you go to fullscreen by pressing Alt + ENTER, you get thrown back to windowed mode if you press just ENTER again.

BTW, would it be feasible to use a menu bar in fullscreen, and showing/hiding it by pressing Esc, like in VisualBoyAdvance or Snes9x for Windows? I would really prefer it over the way you currently choose options in Gens in Windows.

---

### Post by GerbilSoft on 2008-10-29
> **nerdy_girlscout said:**
> sonicretro seems to be down. :(
Now there's just one bug a saw. This isn't new though, it's been in the GNU/Linux port forever I think. Anyway, if you go to fullscreen by pressing Alt + ENTER, you get thrown back to windowed mode if you press just ENTER again.

BTW, would it be feasible to use a menu bar in fullscreen, and showing/hiding it by pressing Esc, like in VisualBoyAdvance or Snes9x for Windows? I would really prefer it over the way you currently choose options in Gens in Windows.

The first part is an issue with how modifier keys are handled between GTK+ and SDL. I'll attempt to fix that for the next release. (You can work around this problem by pressing and releasing Alt after the mode switch is finished.)

The second part, I'm not sure if that can be fixed easily. Fullscreen mode uses plain SDL without GTK+, so I can't easily add a menu bar. I am considering adding an on-screen display though, similar to the type found on a cable box.

---

### Post by nerdy_girlscout on 2008-10-29
Is it hard to use GTK and SDL in fullscreen? I don't have any coding experience so I don't know. But most important is the issue with input that I mentioned though. Thanks!

---

### Post by Disreali on 2008-10-29
I would like to second nerdy_girlscout's request, yet understand that they may be difficult. I'm no coder either.

Your version of Gens is AWESOME!!  It does not flicker on my system and the menus are actually usable. :)  I can also use OpenGL with this version. I thank and encourage you to continue your efforts. Thanks

---

### Post by GerbilSoft on 2008-10-29
> **Disreali said:**
> I would like to second nerdy_girlscout's request, yet understand that they may be difficult. I'm no coder either.

Your version of Gens is AWESOME!!  It does not flicker on my system and the menus are actually usable. :)  I can also use OpenGL with this version. I thank and encourage you to continue your efforts. Thanks
Thanks. :)

Unfortunately, it doesn't seem like it's possible to use GTK+ menus in a fullscreen SDL application. However, I am planning on writing custom menus for an OSD interface later on.

---

### Post by chris79 on 2008-10-29
Great Job.

But how can i compile for amd64 on ubuntu intrepid.
./Configure quits with this errormessage:
***
configure: error: 64-bit is currently not supported.
***
Any Ideas what i did wrong? 


Greetings

---

### Post by GSZX1337 on 2008-10-29
> **chris79 said:**
> Great Job.

But how can i compile for amd64 on ubuntu intrepid.
./Configure quits with this errormessage:
***
**configure: error: 64-bit is currently not supported.**
***
Any Ideas what i did wrong? 


Greetings

That's what's wrong.

---

### Post by GerbilSoft on 2008-10-29
> **chris79 said:**
> Great Job.

But how can i compile for amd64 on ubuntu intrepid.
./Configure quits with this errormessage:
***
configure: error: 64-bit is currently not supported.
***
Any Ideas what i did wrong? 


Greetings
Gens currently has a ton of 32-bit assumptions, such as storing pointers in integers and the use of x86 assembly code. Unfortunately, this makes it impossible to compile Gens as a 64-bit application. You should be able to use the 32-bit version if you have the appropriate 32-bit compatibility libraries installed.

---

### Post by nerdy_girlscout on 2008-10-30
> **GerbilSoft said:**
> Thanks. :)

Unfortunately, it doesn't seem like it's possible to use GTK+ menus in a fullscreen SDL application. However, I am planning on writing custom menus for an OSD interface later on.

I don't know if I've seen a complete interface in OSD before. I'll see how it turns out. :3

About 64-bit, will it be supported when you've replaced enough asm code?

---

### Post by GerbilSoft on 2008-10-30
> **nerdy_girlscout said:**
> I don't know if I've seen a complete interface in OSD before. I'll see how it turns out. :3

About 64-bit, will it be supported when you've replaced enough asm code?
Yes, 64-bit will be supported once all the base asm code is replaced. (Starscream, the 68000 emulator, is going to be a pain - it's a C program that emits assembly.) I will retain the asm code for most of the renderers as a compile-time option though, so x86 users can take advantage of that. Other architectures will use C++ versions of said renderers. (On 64-bit, the C++ version might actually be faster than the 32-bit asm version because of larger registers.)

---

### Post by megamaced on 2008-10-31
Sorry if I've missed something but my favourite game on the Megadrive does not work on Gens/GS - Super Street Fighter 2: The New Challengers. All I got was a red screen. I've had to revert to the rather inferior Gens 2.15.5 release in order to play it.

---

### Post by GerbilSoft on 2008-10-31
> **megamaced said:**
> Sorry if I've missed something but my favourite game on the Megadrive does not work on Gens/GS - Super Street Fighter 2: The New Challengers. All I got was a red screen. I've had to revert to the rather inferior Gens 2.15.5 release in order to play it.
SSF2:TNC appears to have a custom checksum algorithm. I believe Gens/GS has "Auto Fix Checksum" enabled by default, which uses the standard Sega checksum algorithm; however, since SSF2:TNC doesn't use that algorithm, the game will detect an incorrect checksum and show the red screen.

The solution is to disable "Auto Fix Checksum" in General Options.

---

### Post by GerbilSoft on 2008-11-02
Milestone 5.1 version bump, with a bunch of bugfixes!

---

### Post by mocha on 2008-11-03
I get lots of buzzing noises when trying to run 32X games with the latest version.  I also get 2 bands of garbled graphics on the top and bottom of the screen when using OpenGL rendering.

The last Linux version of Gens that has worked properly for me was 2.15.3 from the other thread on these forums.  2.15.5 must have introduced some OpenGL issues.  The buzzing is another regression probably.  I tried playing with my .asoundrc file and it doesn't help.

---

### Post by GerbilSoft on 2008-11-03
> **mocha said:**
> I get lots of buzzing noises when trying to run 32X games with the latest version.  I also get 2 bands of garbled graphics on the top and bottom of the screen when using OpenGL rendering.

The last Linux version of Gens that has worked properly for me was 2.15.3 from the other thread on these forums.  2.15.5 must have introduced some OpenGL issues.  The buzzing is another regression probably.  I tried playing with my .asoundrc file and it doesn't help.

Which 32X games? The PWM code was rewritten, so that might be the issue. (The only game I tested was Knuckles Chaotix.)

With regards to OpenGL, that's because the top and bottom aren't updated when GL is in use. The same thing happens with other OpenGL emulators, e.g. Mupen64. I will attempt to fix this by adding border color emulation in the next release.

---

### Post by disturbedite on 2008-11-03
@ GerbilSoft
its nice to the oxygen icons in gens.

i'd like throw an idea out there...
you have done a great job on consolidating the shared code between the different OSes. i know of some projects that have further simplified their code base by switching to Qt4 because it is cross platform capable. you could share the same code and interface between windows, linux & mac using Qt4.

just a thought...

---

### Post by GerbilSoft on 2008-11-03
> **disturbedite said:**
> @ GerbilSoft
its nice to the oxygen icons in gens.

i'd like throw an idea out there...
you have done a great job on consolidating the shared code between the different OSes. i know of some projects that have further simplified their code base by switching to Qt4 because it is cross platform capable. you could share the same code and interface between windows, linux & mac using Qt4.

just a thought...

I'd prefer not to use Qt4 on Windows and MacOS because that would require extra dependencies on those platforms. Qt4's core DLL is around 2 MB, so the filesize would be at least double what it is now. Also, the UI isn't really as important as the core emulation functionality, so it's not a big deal. (The largest UI component is the menu system, which is already done.)

---

### Post by mocha on 2008-11-05
> **GerbilSoft said:**
> Which 32X games? The PWM code was rewritten, so that might be the issue. (The only game I tested was Knuckles Chaotix.)

With regards to OpenGL, that's because the top and bottom aren't updated when GL is in use. The same thing happens with other OpenGL emulators, e.g. Mupen64. I will attempt to fix this by adding border color emulation in the next release.


I'll try that Knuckles game and let you know if it still buzzes on my system.  OpenGL in 2.15.3 doesn't have the bands.

---

### Post by disturbedite on 2008-11-05
> **megamaced said:**
> 

And heres an RPM for anyone who needs it:

any chance we could get an updated rpm of version 5.1?

---

### Post by disturbedite on 2008-11-05
please delete. accidental doube post.

---

### Post by megamaced on 2008-11-06
> **disturbedite said:**
> any chance we could get an updated rpm of version 5.1?

Why don't you make one yourself? Its really easy!

Install package "alien":

```
sudo aptitude install alien
```

Download the Gens/GS debian package. Then run:

```
sudo alien -r -k -c gens_*.deb
```

Finally, chown the new RPM so it belongs to you:

```
sudo chown username:groupname gens-*.rpm
```

---

### Post by zelfeed on 2008-11-06
Hello. I have a trouble with enabled sound in Gens 2.14.5/gs-m5. If sound enable, animation very lages, but fps about 60. System Ubuntu 8.10.
And how I could activate netplay in Gens? In Windows netplay is available with kaillera.dll (kaillera and kaiilera-p2p). If linux's gens need kaillera.dll too, what folder I have to put it?

---

### Post by amano on 2008-11-06
Can someone bug a MOTU to get those new versions into the official Ubuntu repositories? It is a shame that all emulation related packages are treated with so low priority: Nestopia for NES, SNES9x for SNES, GENS/GS for the Megadrive, E-UAE for the Amiga, dbgl for DOS...

There are wonderful, shiny versions out in the world, but just ancient, unmaintained cruft in the repositories.

---

### Post by disturbedite on 2008-11-06
> **megamaced said:**
> Why don't you make one yourself? Its really easy!
i know how to use alien. i assumed you were compiling it from source! meh, but now that i know i'll do it myself.

btw, i'm on opensuse now so it would be: sudo zypper in alien...

---

### Post by GerbilSoft on 2008-11-06
> **zelfeed said:**
> Hello. I have a trouble with enabled sound in Gens 2.14.5/gs-m5. If sound enable, animation very lages, but fps about 60. System Ubuntu 8.10.
And how I could activate netplay in Gens? In Windows netplay is available with kaillera.dll (kaillera and kaiilera-p2p). If linux's gens need kaillera.dll too, what folder I have to put it?

Netplay is not supported in Gens/GS right now on either the Windows or Linux versions. I plan on implementing my own netplay protocol sometime in the future.

With regards to the sound issue, make sure that frameskip is set to Auto and the sound frequency is set to 44,100 Hz. Also, try turning on OpenGL and VSync.

---

### Post by Calculon64 on 2008-11-08
Any chance of getting an Ubuntu 8.10 64-bit port?

---

### Post by GerbilSoft on 2008-11-08
> **Calculon64 said:**
> Any chance of getting an Ubuntu 8.10 64-bit port?
As mentioned earlier, Gens currently has a lot of 32-bit x86 assembler code, so it isn't possible to port to 64-bit yet. You should be able to run 32-bit Gens on 64-bit Ubuntu if you have the appropriate compatibility libraries installed. (I don't have a 64-bit system to test on, so I can't test it myself.)

---

### Post by Calculon64 on 2008-11-09
Would someone please post a guide in how to get this emulator running on Ubuntu 8.10 64-bit.  I want to try it really bad since it looks very promising.  Hope this emulator becomes part of the official Ubuntu repositories.  I can't believe how old are the emulators in the Ubuntu repos.

---

### Post by BigSilly on 2008-11-09
> **GerbilSoft said:**
> 
With regards to the sound issue, make sure that frameskip is set to Auto and the sound frequency is set to 44,100 Hz. Also, try turning on OpenGL and VSync.

I did this but still had sound lag and frame rate issues. I've had to go back to official Gens 2.15.5 in order to have smooth gameplay. I only have a simple PC (AMD Sempron 2200+, 768Mb RAM), but I have an Nvidia card (GF 6200 256Mb) with proprietary drivers enabled and emulation is otherwise great for me. Anything else I should look at?

---

### Post by Disreali on 2008-11-09
> **Calculon64 said:**
> Would someone please post a guide in how to get this emulator running on Ubuntu 8.10 64-bit.  I want to try it really bad since it looks very promising.  Hope this emulator becomes part of the official Ubuntu repositories.  I can't believe how old are the emulators in the Ubuntu repos.

See the post here.  

[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by GerbilSoft on 2008-11-10
> **BigSilly said:**
> I did this but still had sound lag and frame rate issues. I've had to go back to official Gens 2.15.5 in order to have smooth gameplay. I only have a simple PC (AMD Sempron 2200+, 768Mb RAM), but I have an Nvidia card (GF 6200 256Mb) with proprietary drivers enabled and emulation is otherwise great for me. Anything else I should look at?
Try setting the bpp setting to 16-bit. The 32-bit color renderer is a bit slower compared to 16-bit, since it's in C++ vs assembly (I've optimized the C++ version somewhat for m5.2, but it's still slower).

Note that this bpp setting is separate from the desktop bpp - it's in Graphics, bpp.

---

### Post by BigSilly on 2008-11-10
> **GerbilSoft said:**
> Try setting the bpp setting to 16-bit. The 32-bit color renderer is a bit slower compared to 16-bit, since it's in C++ vs assembly (I've optimized the C++ version somewhat for m5.2, but it's still slower).

Note that this bpp setting is separate from the desktop bpp - it's in Graphics, bpp.

Ah now that's done the trick. Thanks very much for that. Gens now running nicely on Ubuntu and Mint. :biggrin:

---

### Post by GerbilSoft on 2008-11-16
Milestone 5.2 version bump, with improved performance in 32-bit color and a ton of bugfixes!

---

### Post by robertobech on 2008-11-17
I've been using your emulator for a few weeks on Linux, and I must say it's great, congratulations. I've never really liked the Gens Linux port, but Gens/GS won me.

Any future plans for dumping movies? There is a Gens version that can actually do it:
[http://info.sonicretro.org/Gens_Movie_Test](http://info.sonicretro.org/Gens_Movie_Test)

---

### Post by GerbilSoft on 2008-11-17
> **robertobech said:**
> I've been using your emulator for a few weeks on Linux, and I must say it's great, congratulations. I've never really liked the Gens Linux port, but Gens/GS won me.

Any future plans for dumping movies? There is a Gens version that can actually do it:
[http://info.sonicretro.org/Gens_Movie_Test](http://info.sonicretro.org/Gens_Movie_Test)
I plan to add movie dumping once I get the plugin system working. At first, m6 will have internal plugins only, and they'll only be for renderers; later revisions of m6 will add some more general plugins, such as Game Genie (yes it exists right now, but moving it to a plugin is a better option) and Netplay (custom protocol, not Kaillera).

---

### Post by disturbedite on 2008-11-17
@ GerbilSoft
i have two questions:
1. regarding the removal of the other audio frequencies: was the cause of the lag due to the fact that the other (now removed) frequencies are/were not multiples of 11/22 khz?
2. regardless if that is the case or not, i guess the other audio options from gens32 that i mentioned in a feature request aren't going to be implemented right? (unless the audio lag bugs can be fixed).

gens32 does have surround sound as an audio option, that would be uber cool to have in gens/gs m5!...

---

### Post by GerbilSoft on 2008-11-17
> **disturbedite said:**
> @ GerbilSoft
i have two questions:
1. regarding the removal of the other audio frequencies: was the cause of the lag due to the fact that the other (now removed) frequencies are/were not multiples of 11/22 khz?
2. regardless if that is the case or not, i guess the other audio options from gens32 that i mentioned in a feature request aren't going to be implemented right? (unless the audio lag bugs can be fixed).

gens32 does have surround sound as an audio option, that would be uber cool to have in gens/gs m5!...
That was one of the causes of lag. For the other audio options, I'm planning on adding them with the plugin system for audio processing. The first audio processing plugin I'm going to write is an all-channel mixer. After that, I'll add stuff like surround sound.

---

### Post by disturbedite on 2008-11-18
> **GerbilSoft said:**
> That was one of the causes of lag. For the other audio options, I'm planning on adding them with the plugin system for audio processing. The first audio processing plugin I'm going to write is an all-channel mixer. After that, I'll add stuff like surround sound.
awesome! thanks.

will this/these new audio plugin(s) solve the lag problems completely so that the other audio frequencies could also be reimplemented and new ones possibly added?

---

### Post by GerbilSoft on 2008-11-18
> **disturbedite said:**
> awesome! thanks.

will this/these new audio plugin(s) solve the lag problems completely so that the other audio frequencies could also be reimplemented and new ones possibly added?
The lag problem caused by 16/32/48 kHz is because the audio emulators aren't designed for those frequencies. There really isn't much point in using them anyway, since 44.1 kHz was the maximum frequency output from the original hardware (via SegaCD).

---

### Post by mocha on 2008-11-20
I just tried 5.3 last night, those problems with 32x sound and OpenGL rendering are gone.  Thanks!

---

### Post by GerbilSoft on 2008-11-25
Status report on Gens/GS m6:

- The plugin system is mostly working. The m6 release will only have internal plugins (i.e. built into the binary); a later release will add support for external plugins (*.dll, *.so).

- New renderers: hq3x, hq4x, scale3x, scale4x

- Improved performance with the scale2x renderer. (It now has an MMX-optimized version; previously, it was C++ only.)

- 32-bit color versions of all renderers. (The 32-bit color hq?x renderers unfortunately don't work correctly, so it uses a lookup table to post-process the 16-bit color output to 32-bit color.)

Hopefully, it will be ready for release sometime later this week.

---

### Post by Disreali on 2008-11-25
Yay!  Thanks again for your efforts to make a more robust GENS.

I was wondering if you planned to add SMS/GG emulation like that found in GENS Plus!  I don't know whether the GENS Plus! dev created new code or simply incorparated Charles MacDonald SMSPlus code into his project. I don't know how difficult this may be, but I would definitely like to have a single app to play all my SMS, MD and SegaCD games. 

Thanks again for all that you are doing for Sega retrogamers

---

### Post by mocha on 2008-11-27
> **Disreali said:**
> I was wondering if you planned to add SMS/GG emulation like that found in GENS Plus!  

That would be so cool!!  I use CLI Mednafen for SMS right now.  There's just no good frontend for SMS emulation on Linux.

---

### Post by BigSilly on 2008-11-27
Glad to hear Gens is still getting some love! Just found out today that PLF have put this in their repository, so I can get me some Gens on Mandriva too.

Keep up the good work.

---

### Post by kwash on 2008-12-05
Can Gens/GS load cuesheet files to read BIN/CUE SegaCD images? I cannot do it. The emulator can load the BIN CD image but without the cuesheet the game looses sound from CD Audio tracks that are packed in the BIN.

Can you implement this feature? It would be a nice one. ;)

Thanks for the great effort you're putting into the project.

---

### Post by tghe-retford on 2008-12-06
It's great to see hq3x/4x support forthcoming in Gens GS. It was one of the main reasons I use Kega Fusion via Wine (though it is a no-go at the moment because of sound issues), and hq4x through Gens (like I can with other Linux native emulators) should be awesome.

The one thing that would clinch it for me is a problem that has always inflicted Gens since I first used it on Windows. Playing on a Mega CD game, after the current track ends the next track on the CD would play, when it should repeat the current track. When I pause, and then unpause, Gens will play the next track from the beginning, instead of continuing the current track where it left off.

If this can be fixed, then I can fully use Gens GS and not need to rely on Kega Fusion (one less Windows app). Keep up the great work.

---

### Post by GSZX1337 on 2008-12-06
> **mocha said:**
> That would be so cool!!  I use CLI Mednafen for SMS right now.  There's just no good frontend for SMS emulation on Linux.

Have you tried [gOsmose]("http://ubuntuforums.org/showthread.php?t=753863")?

---

### Post by mocha on 2008-12-06
> **GSZX1337 said:**
> Have you tried [gOsmose]("http://ubuntuforums.org/showthread.php?t=753863")?

Hadn't heard of that.  Thanks..

---

### Post by GerbilSoft on 2008-12-07
> **kwash said:**
> Can Gens/GS load cuesheet files to read BIN/CUE SegaCD images? I cannot do it. The emulator can load the BIN CD image but without the cuesheet the game looses sound from CD Audio tracks that are packed in the BIN.

Can you implement this feature? It would be a nice one. ;)

Thanks for the great effort you're putting into the project.
It's planned, but for now you can use cdemu.

> **tghe-retford said:**
> 
The one thing that would clinch it for me is a problem that has always inflicted Gens since I first used it on Windows. Playing on a Mega CD game, after the current track ends the next track on the CD would play, when it should repeat the current track. When I pause, and then unpause, Gens will play the next track from the beginning, instead of continuing the current track where it left off.

I've noticed this too. I'll attempt to take a look at it and figure out what's wrong. The CD code in general needs a rewrite (in particular, port the Linux code to libcdio so it works on BSD and OS X).

---

### Post by maybeway36 on 2008-12-07
Is there a feature to automatically save the state when the emulator exits, and load it again when it is restarted with the same ROM?

---

### Post by GerbilSoft on 2008-12-07
> **maybeway36 said:**
> Is there a feature to automatically save the state when the emulator exits, and load it again when it is restarted with the same ROM?
There isn't right now, but that does sound like an interesting idea.

Also, Milestone 6 is out. See the first post for more information.

---

### Post by GSZX1337 on 2008-12-08
> **GerbilSoft said:**
> There isn't right now, but that does sound like an interesting idea.

Also, Milestone 6 is out. See the first post for more information.

If you do implememnt this feature, could you have it where an alert box pops up asking you if you'd like to make a save state? (kind of like in a image-editing app)

---

### Post by robertobech on 2008-12-08
Thanks again for such a good work. I hope the plugin system evolves, as it looks quite promising.

---

### Post by ezekiel000 on 2008-12-09
Will support for Vorbis Ogg soundtracks for Mega CD games be added to Gens/GS?

---

### Post by mocha on 2008-12-10
With regards to SegaCD emulation, is there any chance you can fix the game Snatcher?  I found this thread from almost 3 years ago, I'm experiencing the same problem.  Thanks.

[http://forums.darkmystics.com/showthread.php?p=9705]("http://forums.darkmystics.com/showthread.php?p=9705")

---

### Post by mister_k81 on 2008-12-11
Sonic CD also seems to have an odd sound bug too. When entering or exiting the mode 7-ish 3D bonus stages while playing, half the sound effects will disappear and stay that way for the remainder of the game. It's not a huge issue, and can be solved by saving your progress to a save state, then restarting the game and reloading. But, I thought it's still worth mentioning. 

Also, I'm using the actual North American CD and not an ISO/bin file... though I did also try an ISO rom, and the same issue is there as well.

Other then that, all other Sega CD games that I've tried so far work great! (Final Fight CD, Silpheed, Earthworm Jim: Special Edition, Terminator) Aside from the music skipping problem when pausing, which was already mentioned. 

And this version of Gens fixes the biggest problem I had with the one that megamaced was maintaining, the frame rate. In that other Gens, the frame rate would constantly jump anywhere between 50 to over 70fps and make games look very stuttery and hard to play. This version is locked at a much steadier 60fps with very minor jumps. 

Gens/GS is fantastic so far... keep up the good work. :grin:

---

### Post by BigSilly on 2008-12-12
Gens/GS is absolutely fantastic. My heartfelt thanks to Gerbilsoft for the hard work and devotion. One of the best Linux emulators there is imho.

I recently upgraded to the new M6 version, and it's been fantastic. However, since trying out some Sega CD games it's suddenly started popping up this error -

```
Error in ZIP file: 
Unexpected end of file.
```

I get this message every time I start Gens/GS now. The games all work in spite of the error message. I'm sure it's something I've done wrong somewhere, so if you could let me know what this is and how to fix it that would be great.

My thanks again!

---

### Post by GerbilSoft on 2008-12-12
> **BigSilly said:**
> 
I get this message every time I start Gens/GS now. The games all work in spite of the error message. I'm sure it's something I've done wrong somewhere, so if you could let me know what this is and how to fix it that would be great.

My thanks again!

This is a limitation with how the "ROM History" feature works. On startup, it checks all ROMs in the ROM history to determine the type of ROM, so it can add "[MD]", "[32X]", etc. to the ROM name. For m6.1, I'll have it cache the ROM type, so it won't need to check the ROM anymore.

With regards to the SegaCD questions:

- MP3 support is a horrible mess right now. I'm planning on porting it over to lame or libmad eventually. Additionally, adding Ogg Vorbis support shouldn't be too hard once I clean up the MP3 interface.

- I don't have a copy of Snatcher, so I can't take a look at that. However, I'm suspecting it's an issue with the MP3 code in general.

- I do remember encountering the sound-effects-dies bug in Sonic CD. I can't remember how to trigger it, and haven't encountered it recently.

---

### Post by BigSilly on 2008-12-12
> **GerbilSoft said:**
> This is a limitation with how the "ROM History" feature works. On startup, it checks all ROMs in the ROM history to determine the type of ROM, so it can add "[MD]", "[32X]", etc. to the ROM name. For m6.1, I'll have it cache the ROM type, so it won't need to check the ROM anymore.

Ah, I've got you. I've deleted the ROM history in the .gens config file, and it's not giving me the error anymore. Thanks very much for that. :KS

---

### Post by bolingw on 2008-12-15
Hi guys.

I've just installed the "Gens_2.15.5-gs-m6-1_i386" package and have been trying the emulator out. For some reason, the bottom part of my screen is cut off (i have a 1280*800 laptop screen) when I go into full screen mode. I've tried the stretching but all its options seem to have no effect on the mode and I could not find other options solving the problem. There must be mechanics within the program for twisting screen ratio, so I've wondering what I'm missing out here.

ty.

---

### Post by GerbilSoft on 2008-12-16
> **bolingw said:**
> Hi guys.

I've just installed the "Gens_2.15.5-gs-m6-1_i386" package and have been trying the emulator out. For some reason, the bottom part of my screen is cut off (i have a 1280*800 laptop screen) when I go into full screen mode. I've tried the stretching but all its options seem to have no effect on the mode and I could not find other options solving the problem. There must be mechanics within the program for twisting screen ratio, so I've wondering what I'm missing out here.

ty.
Try using OpenGL mode, and set a custom GL resolution of 1280x800.

I need to rework the video mode options, including adding a separate "Full Screen Resolution" option.

EDIT: [2008/12/18] I've ported Gens/GS's physical CD-ROM support to libcdio. libcdio is cross-platform (Linux, Windows ASPI, Windows NT SPTI, MacOS X, BSD, Solaris), and fully supports BIN/CUE, BIN/TOC, and NRG format disc images. This means that you'll be able to use BIN/CUEs with audio tracks in Gens/GS m6.1. :)

---

### Post by amano on 2008-12-21
Since no MegaDrive emulator supports it: Is it possible to use Blargg's NTSC filter for MegaDrive/Genesis emus as well?

---

### Post by GerbilSoft on 2008-12-22
> **amano said:**
> Since no MegaDrive emulator supports it: Is it possible to use Blargg's NTSC filter for MegaDrive/Genesis emus as well?
Blargg does have a Genesis NTSC filter, but that would require adding support for "pre-render" plugins. That is, a plugin that modifies the original source image before going to the main renderer. I am planning on adding support for this later on, but it won't be done immediately.

---

### Post by disturbedite on 2008-12-22
> **GerbilSoft said:**
> Blargg does have a Genesis NTSC filter, but that would require adding support for "pre-render" plugins. That is, a plugin that modifies the original source image before going to the main renderer. I am planning on adding support for this later on, but it won't be done immediately.

thanks amano for asking this & thanks GerbilSoft for answering cuz i was wondering this same thing...

---

### Post by ProcyonSJJ on 2009-01-12
Hi, I'm relatively new to Ubuntu.  I'm very glad I made the switch from windows, and I don't mind compiling my own stuff, but could someone please provide a step by step walkthrough of how to succeed in making Gens on a 64-bit platform?  I saw the link to the other thread about getlibs, but I don't see how that helps if you're trying to build from source.  It would be greatly appreciated.  Thanks very much.

Procyon

_Update:_ OK, I found out about the --force-architecture option.  So the way I was able to install it was by downloading the deb file from sonicretro.org, and running

```

sudo dpkg -i --force-architecture Gens-2.15.5-gs-m6-1_i386.deb

```

and that did the trick.  Tough to nail down a steady framerate, but it's far better than the alternatived.  Dgen gives a segmentation fault, XE gives error after error, and Generator won't run at 60FPS.  Only thing comparable performance wise is SDLMESS.

---

### Post by josh5769 on 2009-01-14
First off, thank you for this emu! I'm only having one small problem with the sound. I'm getting:

Can't step back 124!

every time the game loads or changes tracks. There is also a huge lag in the sound. I've tried every workaround I could find, adjusted and even reinstalled, but I just can't get it to work. 

The sound effects seem to be fine.

Oh, I'm playing Lunar: The Silver Star from ISO

Thanks again for all your hard work. :)

---

### Post by GerbilSoft on 2009-01-14
> **josh5769 said:**
> Can't step back 124!
That happens if you're using ISO/MP3. Gens/GS's MP3 library has known issues. I plan on replacing it with a better MP3 library later.

With regards to sound being out of sync, make sure you're not using PulseAudio. Also, set the sound rate to 44,100 Hz.

---

### Post by josh5769 on 2009-01-14
You would be right on the ISO/mp3. I appreciate the response, thanks again for all your hard work! :)

---

### Post by disturbedite on 2009-01-19
> **GerbilSoft said:**
> Yes, 64-bit will be supported once all the base asm code is replaced. (Starscream, the 68000 emulator, is going to be a pain - it's a C program that emits assembly.) I will retain the asm code for most of the renderers as a compile-time option though, so x86 users can take advantage of that. Other architectures will use C++ versions of said renderers. (On 64-bit, the C++ version might actually be faster than the 32-bit asm version because of larger registers.)

i recently rebuilt my PC and am on a 64bit platform so now i am interested in gens going 64bit. i know i can force the architecture to install it, but i'm curious:
do you have an ETA on this? are you working on it? or is it something that is far out in the future?

---

### Post by GerbilSoft on 2009-01-20
> **disturbedite said:**
> i recently rebuilt my PC and am on a 64bit platform so now i am interested in gens going 64bit. i know i can force the architecture to install it, but i'm curious:
do you have an ETA on this? are you working on it? or is it something that is far out in the future?
Honestly, 64-bit provides no real advantage for Gens. There's really no point in spending the extra effort to get 64-bit working right now.

That being said, I'm in the process of porting the Z80 emulator to C. After that, I'll need to port/rewrite the 68000 emulator and the VDP emulator to get Genesis and SegaCD emulation working. 32X emulation will require porting the SH2 core from assembler to C. That, and I have to fix all the 32-bit pointer issues. (There's plenty of hard-coded 32-bit pointer assumptions in Gens.)

---

### Post by disturbedite on 2009-01-20
> **GerbilSoft said:**
> Honestly, 64-bit provides no real advantage for Gens. There's really no point in spending the extra effort to get 64-bit working right now.

That being said, I'm in the process of porting the Z80 emulator to C. After that, I'll need to port/rewrite the 68000 emulator and the VDP emulator to get Genesis and SegaCD emulation working. 32X emulation will require porting the SH2 core from assembler to C. That, and I have to fix all the 32-bit pointer issues. (There's plenty of hard-coded 32-bit pointer assumptions in Gens.)

well, it would be nice to have a 64bit gens for uniformity if nothing else on 64bit platforms.

thanks for the info.

could you elaborate a little more on why there wouldn't be an advantage if gens were ported to 64bit? i'm not a programmer, but i am a computer technician, so you don't have to dumb it down. i'm curious.

---

### Post by GerbilSoft on 2009-01-20
> **disturbedite said:**
> could you elaborate a little more on why there wouldn't be an advantage if gens were ported to 64bit? i'm not a programmer, but i am a computer technician, so you don't have to dumb it down. i'm curious.
The main advantage of 64-bit is high memory support (>4GB without PAE). Gens only uses around ~20 MB RAM (less if I rework the way memory is allocated for the ROM image), so using 64-bit pointers will actually increase memory usage, since pointers will take up 8 bytes instead of 4. The only part of the program that could really benefit from more registers is the rendering system (hq2x, etc), but there would be a larger gain from using SSE/SSE2/etc, which works in 32-bit mode anyway (and involves rewriting the code).

---

### Post by jmacdonagh on 2009-01-26
This package works great, but Gens/GS doesn't appear to want to play nice with my Xbox 360 controller. I can't map input to the d pad. For a lot of games, I prefer it over the left analog stick. Running jstest shows that the axes are going off correctly, but Gens/GS appears to only support axes 0-5, not 6/7 which correspond to the d pad.

I've been trying to manually edit my gens.cfg file and incrementing the P1.Up hex code, but none that I have tried have worked. Is there some documentation on how to specify which axes to use in gens.cfg?

---

### Post by GerbilSoft on 2009-01-26
> **jmacdonagh said:**
> This package works great, but Gens/GS doesn't appear to want to play nice with my Xbox 360 controller. I can't map input to the d pad. For a lot of games, I prefer it over the left analog stick. Running jstest shows that the axes are going off correctly, but Gens/GS appears to only support axes 0-5, not 6/7 which correspond to the d pad.

I've been trying to manually edit my gens.cfg file and incrementing the P1.Up hex code, but none that I have tried have worked. Is there some documentation on how to specify which axes to use in gens.cfg?
Gens/GS currently doesn't support more than 6 axes per controller on Linux, and its current mapping system won't allow for more than 6 axes. I'm going to redo the way the joystick configuration is mapped for both Windows and Linux for the next version.

For reference, here's the current encoding (using a 16-bit value):

0x1JTW

where:
1 == always set to 1 to indicate joystick input.
J == joystick number.
T == input type. 0 == axis, 1-7 == button, 8 == POV hat (Win32 only).
W == which axis/button.

Axes are actually split into two values; one for negative (e.g. up), and one for positive (e.g. down). Since Gens currently doesn't use 0 as an axis value, that leaves 1-15 as usable, which allows for 7 axes. (Only 6 are currently programmed in for consistency.)

I'm considering changing the format to something like this: (binary)

1TTT JJJJ WWWW WWWW

1 == high bit is always 1 to indicate joystick input.
T == input type. 0 == axis, 1 == button, 2 == POV hat.
J == joystick number.
W == which axis/button.

This will allow for up to 256 buttons and 128 axes per controller. I'm also going to change the semantics to use 0 as an axis number.

The only downside to switching to this method is that [s]it will require reconfiguration for existing setups.[/s] the new configurations will not work with older versions of Gens. (I'll add code to automatically convert old-format joystick configurations to the new format.)

EDIT: Initial support for the extended format is now in the latest git master version, which is available at [http://gs_server.gerbilsoft.ddns.info/cgi-bin/gitweb.cgi?p=gens.git;a=summary](http://gs_server.gerbilsoft.ddns.info/cgi-bin/gitweb.cgi?p=gens.git;a=summary) . Note that the current master version has a bunch of other changes, including external plugins (shared libraries). Also, the Game Genie plugin is currently non-functional. (It shows a basic UI, but it's not possible to add codes, and the codes don't have any effect.)

[s]Also, the initial support doesn't automatically convert old-format configurations to the new format yet.[/s]

EDIT 2: I added support for POV Hat switches in the SDL input handler. (I haven't been able to test it, since I don't have any input devices that report POV Hat switches on Linux, but it *should* work.) Also, I added a function to convert old-format configurations to the new format. (The function is automatically called when loading the Gens configuration on startup.) It works for buttons and axes right now, but not POV Hat switches.

(Incidentally, most devices that show POV Hat switches on Windows simply report them as regular axes on Linux. I wouldn't be surprised if the Xbox 360 controller did the same thing.)

---

### Post by GerbilSoft on 2009-02-10
While redoing the controller system, I decided to redo the "Controller Configuration" dialog to make it easier to see what the controller input is being recognized as.

Old version:
[img]http://www.soniccenter.org/gerbilsoft/gens/gens-gs-m6-controller-configuration.png[/img]

New version:
[img]http://www.soniccenter.org/gerbilsoft/gens/gens-gs-r6+-72619445-controller-configuration.png[/img]

Among other things, the new version lets you see the key code and the actual key that it maps to, plus it lets you configure devices one key at a time.

Edit: I originally intended for the "Input Device" dropdown to let you limit devices for changing the key configuration, but now I think that might be unnecessary and confusing, since it only affects new configurations, not existing ones. However, listing the available input devices is still useful, so I'll probably change it to a listbox and move it underneath the controller ports.

---

### Post by DancemasterGlenn on 2009-02-11
Will this new system still allow for an "all at once" reconfiguration? It's not a huge deal, but I do enjoy the ease of hitting one reconfigure button and choosing my inputs all in a row.

Thanks for your continued work, by the way. It's great to see solid Gens development after all this time.

---

### Post by GerbilSoft on 2009-02-12
> **DancemasterGlenn said:**
> Will this new system still allow for an "all at once" reconfiguration? It's not a huge deal, but I do enjoy the ease of hitting one reconfigure button and choosing my inputs all in a row.
[img]http://www.soniccenter.org/gerbilsoft/gens/gens-gs-r6+-823ff6a9-controller-configuration.png[/img]

Yes, it will. :) I added two new buttons. One lets you configure all inputs in one shot (each one prompts you to press a key); the other lets you clear all buttons for a controller, which is useful for disabling the second player. Later, I may add a feature to actually "unplug" controllers from the console, but that requires low-level code changes.

Also, I received a suggestion to add checkboxes next to the input devices to allow filtering devices when using the "Change" button, so I will attempt to do that. It'd be especially useful in my case, since you can see that my ThinkPad's accelerometer is registered as a joystick, so if my laptop was tilted the wrong way, it'd register as a joystick axis movement. :)

---

### Post by DancemasterGlenn on 2009-02-12
Looks nice, especially resized to get rid of the unnecessary empty spaces. Thanks for adding the "all at once" option. Looking forward to the next release!

---

### Post by Fisher on 2009-02-27
Very cool!!!
But, What about milestone 6?? Is there a way to compile it o Ubutu 7.04??
I have found something, but it's in japanese ana I could not understand!!!

---

### Post by GerbilSoft on 2009-03-02
> **Fisher said:**
> Very cool!!!
But, What about milestone 6?? Is there a way to compile it o Ubutu 7.04??
I have found something, but it's in japanese ana I could not understand!!!
It should be possible to compile it on 7.04, but there may be some compatibility issues that I haven't noticed due to not testing it there. If you can get a build log, I can fix these issues.

Also, I'll hopefully have Release 7 out sometime in the next few weeks. Release 7 introduces the external MDP plugin system, which is going to remain binary-compatible for a while, so I want to make sure I get it right the first time.

---

### Post by jgreen6883 on 2009-03-03
I'm having problems compiling Milestone 6. ./configure runs fine, but make ends with this..

        then mv -f "ui/gtk/gens/.deps/gens-gens_window_callbacks.Tpo" "ui/gtk/gens/.deps/gens-gens_window_callbacks.Po"; else rm -f "ui/gtk/gens/.deps/gens-gens_window_callbacks.Tpo"; exit 1; fi
ui/gtk/gens/gens_window_callbacks.cpp: In function ‘void gens_window_drag_data_received(GtkWidget*, GdkDragContext*, gint, gint, GtkSelectionData*, guint, guint, void*)’:
ui/gtk/gens/gens_window_callbacks.cpp:127: error: ‘g_uri_unescape_string’ was not declared in this scope
ui/gtk/gens/gens_window_callbacks.cpp: At global scope:
ui/gtk/gens/gens_window_callbacks.cpp:93: warning: unused parameter ‘widget’
ui/gtk/gens/gens_window_callbacks.cpp:93: warning: unused parameter ‘x’
ui/gtk/gens/gens_window_callbacks.cpp:93: warning: unused parameter ‘y’
ui/gtk/gens/gens_window_callbacks.cpp:93: warning: unused parameter ‘target_type’
ui/gtk/gens/gens_window_callbacks.cpp:93: warning: unused parameter ‘data’
ui/gtk/gens/gens_window_callbacks.cpp:149: warning: unused parameter ‘x’
ui/gtk/gens/gens_window_callbacks.cpp:149: warning: unused parameter ‘y’
ui/gtk/gens/gens_window_callbacks.cpp:149: warning: unused parameter ‘user_data’
ui/gtk/gens/gens_window_callbacks.cpp:171: warning: unused parameter ‘widget’
ui/gtk/gens/gens_window_callbacks.cpp:171: warning: unused parameter ‘event’
ui/gtk/gens/gens_window_callbacks.cpp:171: warning: unused parameter ‘user_data’
ui/gtk/gens/gens_window_callbacks.cpp:185: warning: unused parameter ‘widget’
ui/gtk/gens/gens_window_callbacks.cpp:185: warning: unused parameter ‘event’
ui/gtk/gens/gens_window_callbacks.cpp:185: warning: unused parameter ‘user_data’
make[3]: *** [ui/gtk/gens/gens-gens_window_callbacks.o] Error 1

---

### Post by GerbilSoft on 2009-03-04
> **jgreen6883 said:**
> I'm having problems compiling Milestone 6. ./configure runs fine, but make ends with this..

        then mv -f "ui/gtk/gens/.deps/gens-gens_window_callbacks.Tpo" "ui/gtk/gens/.deps/gens-gens_window_callbacks.Po"; else rm -f "ui/gtk/gens/.deps/gens-gens_window_callbacks.Tpo"; exit 1; fi
ui/gtk/gens/gens_window_callbacks.cpp: In function ‘void gens_window_drag_data_received(GtkWidget*, GdkDragContext*, gint, gint, GtkSelectionData*, guint, guint, void*)’:
ui/gtk/gens/gens_window_callbacks.cpp:127: error: ‘g_uri_unescape_string’ was not declared in this scope
ui/gtk/gens/gens_window_callbacks.cpp: At global scope:
ui/gtk/gens/gens_window_callbacks.cpp:93: warning: unused parameter ‘widget’
ui/gtk/gens/gens_window_callbacks.cpp:93: warning: unused parameter ‘x’
ui/gtk/gens/gens_window_callbacks.cpp:93: warning: unused parameter ‘y’
ui/gtk/gens/gens_window_callbacks.cpp:93: warning: unused parameter ‘target_type’
ui/gtk/gens/gens_window_callbacks.cpp:93: warning: unused parameter ‘data’
ui/gtk/gens/gens_window_callbacks.cpp:149: warning: unused parameter ‘x’
ui/gtk/gens/gens_window_callbacks.cpp:149: warning: unused parameter ‘y’
ui/gtk/gens/gens_window_callbacks.cpp:149: warning: unused parameter ‘user_data’
ui/gtk/gens/gens_window_callbacks.cpp:171: warning: unused parameter ‘widget’
ui/gtk/gens/gens_window_callbacks.cpp:171: warning: unused parameter ‘event’
ui/gtk/gens/gens_window_callbacks.cpp:171: warning: unused parameter ‘user_data’
ui/gtk/gens/gens_window_callbacks.cpp:185: warning: unused parameter ‘widget’
ui/gtk/gens/gens_window_callbacks.cpp:185: warning: unused parameter ‘event’
ui/gtk/gens/gens_window_callbacks.cpp:185: warning: unused parameter ‘user_data’
make[3]: *** [ui/gtk/gens/gens-gens_window_callbacks.o] Error 1

g_uri_escape_string() was added in GLib 2.16, which I found out during r7 development. Ubuntu 8.04 (Hardy) has GLib 2.16.3, but Gutsy has 2.14.1.

Here are the two patches in the Gens/GS git repository that fix this:
[http://gs_server.gerbilsoft.ddns.info/cgi-bin/gitweb.cgi?p=gens.git;a=commitdiff;h=fcd92e5711929586796f8905370b3afe525276bd;hp=91d48a024d556a20cb6c17552902b047495f6738](http://gs_server.gerbilsoft.ddns.info/cgi-bin/gitweb.cgi?p=gens.git;a=commitdiff;h=fcd92e5711929586796f8905370b3afe525276bd;hp=91d48a024d556a20cb6c17552902b047495f6738)
[http://gs_server.gerbilsoft.ddns.info/cgi-bin/gitweb.cgi?p=gens.git;a=commitdiff;h=f8fb428dc77e4580e86914e97062eac345a1ead5;hp=fcd92e5711929586796f8905370b3afe525276bd](http://gs_server.gerbilsoft.ddns.info/cgi-bin/gitweb.cgi?p=gens.git;a=commitdiff;h=f8fb428dc77e4580e86914e97062eac345a1ead5;hp=fcd92e5711929586796f8905370b3afe525276bd)

I'm not sure if they'll apply cleanly to m6, and I can't test it at the moment.

---

### Post by BigSilly on 2009-03-14
> **disturbedite said:**
> i recently rebuilt my PC and am on a 64bit platform so now i am interested in gens going 64bit. i know i can force the architecture to install it, but i'm curious:
do you have an ETA on this? are you working on it? or is it something that is far out in the future?

Same here, so I'd just like to add my shout for a 64 bit version. I've just recently decided to try out 64 bit Ubuntu alongside my 32 bit install. I really like it even though I only have 3GB RAM. It's definitely faster etc. It'd be nice to not have to dual boot with a 32 bit install just to play Gens/GS (force isn't working so good for me), so if you don't mind I'll stand here and cheer-lead for a 64 bit Gens/GS!

Well done for this excellent emu Gerbilsoft. Can't wait to try out the new version.

---

### Post by Grishka on 2009-03-14
> **BigSilly said:**
> Same here, so I'd just like to add my shout for a 64 bit version. I've just recently decided to try out 64 bit Ubuntu alongside my 32 bit install. I really like it even though I only have 3GB RAM. It's definitely faster etc. It'd be nice to not have to dual boot with a 32 bit install just to play Gens/GS (force isn't working so good for me), so if you don't mind I'll stand here and cheer-lead for a 64 bit Gens/GS!

Well done for this excellent emu Gerbilsoft. Can't wait to try out the new version.

rewriting the code for 64-bit isn't a trivial task, I'd imagine, and Gens/GS works very well on a 64-bit Ubuntu. installing it using dpkg with --force-architecture and using getlibs to install necessary 32-bit libraries does the trick.

---

### Post by BigSilly on 2009-03-14
> **Grishka said:**
> rewriting the code for 64-bit isn't a trivial task, I'd imagine, and Gens/GS works very well on a 64-bit Ubuntu. installing it using dpkg with --force-architecture and using getlibs to install necessary 32-bit libraries does the trick.

I wouldn't have thought it was a trivial task. I didn't imply that anyway, and was just politely supporting the emu with a vote for a 64 bit version. I'm using the 32 bit version at the moment and love it, but just wanted to support Gerbilsoft's previously stated intention that he will release a 64 bit version eventually.

I don't think that warranted a telling off. Do you?

---

### Post by Grishka on 2009-03-14
> **BigSilly said:**
> I wouldn't have thought it was a trivial task. I didn't imply that anyway, and was just politely supporting the emu with a vote for a 64 bit version. I'm using the 32 bit version at the moment and love it, but just wanted to support Gerbilsoft's previously stated intention that he will release a 64 bit version eventually.

I don't think that warranted a telling off. Do you?

that, a telling off?
a bow for your gentle soul;
it's like a pistil.

like stated before,
rewriting is an option.
though stars must align.

so much else to do,
and just a slight advantage.
gerbils sleep for now.

---

### Post by TheIdiotThatIsMe on 2009-03-31
I use Gens (regular) on Windows, and just found this for Ubuntu (one less thing to have to go back to Windows for...). Anyways, I have save games in the .gs0 and .srm formats for my favorite game, and I was wondering if I could load them in Gens\GS so I don't have to restart my games, or if there is a place I can put them so that Gens\GS recognizes them when starting the rom?

---

### Post by GerbilSoft on 2009-04-07
> **TheIdiotThatIsMe said:**
> I use Gens (regular) on Windows, and just found this for Ubuntu (one less thing to have to go back to Windows for...). Anyways, I have save games in the .gs0 and .srm formats for my favorite game, and I was wondering if I could load them in Gens\GS so I don't have to restart my games, or if there is a place I can put them so that Gens\GS recognizes them when starting the rom?
Savestates and SRAM files are usually stored in ~/.gens/.

---

### Post by nashienet on 2009-04-10
quick question, whenever i launch gens now the window is maximized (no window controls visible) how can i turn it back into a regular window? Is there a keyboard shortcut?

---

### Post by GerbilSoft on 2009-04-10
> **nashienet said:**
> quick question, whenever i launch gens now the window is maximized (no window controls visible) how can i turn it back into a regular window? Is there a keyboard shortcut?
The keyboard shortcut for fullscreen is Alt+Enter. Note that there's a bug where the modifier keys sometimes get stuck, so if that happens, try pressing and releasing the Alt key.

---

### Post by wsamh on 2009-05-05
Thank you. It worked.

---

### Post by maybeway36 on 2009-05-20
I'm having problems compiling this on Tiny Core Linux. I installed the GTK2 dev libraries and the standard compilation tools and ran this command:
```
env CPPFLAAGS="-I/usr/local/include/gtk-2.0/gtk" ./configure
```
But I got errors saying it can't find the GTK libraries.
Here's my config.log:
[http://pastebin.com/f70f84bf1](http://pastebin.com/f70f84bf1)

---

### Post by farukali on 2009-05-21
thanks for giving the downloading option

---

### Post by Phyds on 2009-05-29
With Gens/GS Milestone 6, the F5 (quick save) and F8 (quick load) keys do nothing when playing in full screen. But when playing in a window, they work.

---

### Post by Phyds on 2009-05-30
Another small bug with save/load. In Linux, when I save a state with **Save State As** and after try to load, the file saved previously is not seen in the loading window. I see however from a terminal that the file is there but without extension. That's maybe the problem, the **Save State As** doesn't give an extension to the file.

---

### Post by brain51983 on 2009-06-26
I can't see any menu to choose open file as well as change settings. Is this normal? I'm running Ubuntu 9.04 and using Compiz and Avant Window Navigator.

[[IMG]http://img218.imageshack.us/img218/9762/screenshotntb.th.png[/IMG]](http://img218.imageshack.us/i/screenshotntb.png/)

---

### Post by disturbedite on 2009-06-26
> **brain51983 said:**
> I can't see any menu to choose open file as well as change settings. Is this normal? I'm running Ubuntu 9.04 and using Compiz and Avant Window Navigator.

try disabling compositing. i have to do that in kde4 or it crashes plasma.

---

### Post by Beware The Birchmen on 2009-07-02
Is the file in the OP the best version of Gens/GS to get still for  ubuntu 9.04? or is there a new link/version somewhere?

---

### Post by Nevon on 2009-07-02
> **Beware The Birchmen said:**
> Is the file in the OP the best version of Gens/GS to get still for  ubuntu 9.04? or is there a new link/version somewhere?

It's in the repositories. Just type sudo apt-get install gens

---

### Post by CharmyBee on 2009-07-02
> **Nevon said:**
> It's in the repositories. Just type sudo apt-get install gens

Gens isn't Gens/GS.

---

### Post by Loïc2 on 2009-07-02
> **Nevon said:**
> It's in the repositories. Just type sudo apt-get install gens

[In which dimension is this statement true?]("http://packages.ubuntu.com/search?keywords=gens&searchon=names&suite=all&section=all")

---

### Post by Loïc2 on 2009-07-02
> **CharmyBee said:**
> Gens isn't Gens/GS.

Well, gens isn't in the repositories either, and couldn't anyway.

---

### Post by Nevon on 2009-07-02
> **Loïc2 said:**
> Well, gens isn't in the repositories either, and couldn't anyway.

Oops. Guess not. I just did a quick apt-cache search gens (since I knew I had Gens/GS installed) and found it in the list, so I figured I got it from the repositories.

Anyway, here's a deb for you. [http://info.sonicretro.org/images/5/56/Gens_2.15.5-gs-m6-1_i386.deb](http://info.sonicretro.org/images/5/56/Gens_2.15.5-gs-m6-1_i386.deb)

---

### Post by Beware The Birchmen on 2009-07-03
> **Nevon said:**
> It's in the repositories. Just type sudo apt-get install gens
Really? It couldn't find the package for me when I search in Synaptic or do the above command. Any ideas?

---

### Post by BigSilly on 2009-07-03
> **Beware The Birchmen said:**
> Really? It couldn't find the package for me when I search in Synaptic or do the above command. Any ideas?

Yep. Read the posts that followed the one you quoted! :D ;)

---

### Post by Entity` on 2009-09-14
Bump

When is a 9.04 (or 9.10) version coming out or are we going to have to use the --force architecture option?

---

