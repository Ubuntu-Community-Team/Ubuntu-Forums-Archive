---
title: "linux vs windows emu comparison"
date: 2005-07-06
forum: Gaming &amp; Leisure
---

### Post by McQuaid on 2005-07-06
Sadly, I think linux emulation for gaming is a bit of hit and miss.

Just a random rundown of the emu's I always used:

Zsnes & snes9x: Both open source and both available on linux.  Should be fine, right?  Well, I believe it has to do with depending on asm as far as zsnes is concerned as I have had a few freeze ups with the latest that I compiled from source and can barely use it.  I'm going to try the one in the reps next, probably should have tried that first.  And snes9x doesn't use sdl but x11 or svga to access fullscreen which makes it a pain and plus there is no good frontend, well nothing for gtk2 or kde.  Winner: windows.

Epsxe:  Closed source but exits on both windows and linux again.  For the most part you can have the exact same experience in windows or linux.  But I remember having a couple of games that seemed to work better with the d3d driver vs the opengl.  I prefer opengl but as I said some games on the window side performed better with d3d, but haven't done extensive testing yet in linux to see if some games have issues with opengl.  Also since it's closed source it can be a bit cumbersome to install and I don't think there is a way to set it up so it uses your home for saves for memory cards etc.  Make it difficult if you have multiple users and they want their own memory cards etc.  Winner: Tie but with some minor issues.

C64 emus:  Ahh the c64, my childhood.  On the windows side the best for ages was ccs64 which isn't entirely free but the freeware version will play all your games, heck I forget what the pay for version gets you, I think it's to do with actually accessing real 1541 drives, printers or something like that.  For the rest of us the free version is fine.  And for ages ccs64 was the only one with accurate sound, but I believe vice caught up in that department.  And it's open source and exists on both platforms.  Unfortunately, vice on the linux side has one of the clunkiest interfaces I've ever seen and again instead of using sdl it uses some weird video modes and it's a nightmare to even attempt to get fullscreen.  For me I consider it so bad that it's unuseable.  I also tried frodo which was so not ready for prime time I won't go into it.  Winner: windows big time.

Gameboy:  The emu I'll look at here is the visualboyadvance.  Again open source and exits on both.  In linux this actually plays smoother on my box that the windows counterpart.  And it has a good frontend called gnomeboyadvance.  And it uses sdl for graphics so no fullscreen issues.  Well one caveat with sdl in general, it doesn't have a stretch mode so the weird resolutions some consoles use can't actually fill the whole screen so you'll get borders when really the game's display is 4:3.  Directx has had this for ages, I wish they'd implement it in sdl.  But for the most part it's a smoother experience for me with visualboyadance.  Winner: linux Yaaa!!!

Mame:  Ah the king of emu's.  The big kahuna.  On the windows side we've got mame32 and dos mame and a whole wack of other versions.  On the linux side we've got xmame and advmame.  Things are much better here.  We've got sdl, opengl, x11 and svga to access video modes.  Pretty much all the options are there that you'd expect.  But there are issues.  In this distro they can't compile the latest xmame .97 because of xfree86/xorg issues.  And a reasonably good frontend called gxmame hasn't been updated in ages.  Although a beta recently surfaced so at least it's not dead.  I ended up going the advmame mame route and compiled from source.  Thing took over an hour on my box to compile and I ran out of space once during compile.  The frontend it comes with is called advancemenu.  It's meant for using in an actual cabinet and controlling it primarily with a joystick.  It's kind of nice in one way.  You could see what they were going for with just showing the screen shots of the games.  But I found it difficult to show say just my favourite games, it has some rating system but wasn't too intuitive just playing around with it for a few minutes.  Also enabling joystick to use the menu made it wig out on my system with the current game selected just kept going to the left til it reached the top.  Also you have to muck with configs to get a nice video mode.  On the plus side it actually has a software stretch mode so when using overlay mode via sdl, games take up the entire screen which I like.  Overall totally useable but some issues and kinda clunky.  Winner: Tie, I guess but with some issues users have to workaround.

Thats all for now.  I write this just to show my experience with emus in linux and have to admit I'm kinda disappointed as most of these emu's are open source, they just need that extra polish or access video modes in a sane manner.  This is an area where windows shouldn't be one up on linux, but still is overall.

---

### Post by BoyOfDestiny on 2005-07-06
I hear ya. Anyway I've had great luck with the zsnes cvs... but there is one issue I have and can't resolve... Since you know zsnes win, there is an option Vsync, that seems to be absent in the linux version... So I get tearing in games like Megaman X2 or Super Mario All stars... 

Other than that I really want emulation to be stronger than its windows counterparts (since I'm nostalgic =))

---

### Post by McQuaid on 2005-07-06
Hey well maybe I can help.  This afaik only affects opengl but it might affect stuff that uses overlay as well, I don't think I have tearing in non 3d stuff anyways.
Well, it will definitely work if your using opengl mode.

Put this in /etc/environment:
__GL_SYNC_TO_VBLANK=1

That forces vsync for opengl stuff.  Oh but this is nvidia specific not sure what card you have.

---

### Post by keyshawn on 2005-07-07
hey...

I was pretty big into emulation a few years, not as much anymore. Right now, I have my stuff on the windows partition, and haven't had time to play much either. The only emulation I've been into recently is Nester on the dreamcast :smile:

Personally, I haven't had time to try out emulation on linux, but I will eventually.

cya,
skora.

---

### Post by Snipersnest on 2005-07-07
Anybody know if the online versions of SNES9K and such work in linux?   I haven't tried or googled it at all yet. But I host a 100 slot nintendo server on OC line in NYC...be nice if I could use it again.

---

### Post by gil-galad on 2005-07-07
I beat FFVI with the zsnes from the repos.  Worked perfect for me.  :)

---

### Post by Akir on 2005-07-07
Everything emulated doesn't work as well on linux as it did for me on windows. I don't know why, but if I had to guess, I'd say it's because the developers spend more time on windows because it is (unfortunately) more popular then linux. Maybe I'll get a faster computer that these will work on better. Or I'll actually spend time on compilation to speed it up instead of using packages....

By the way, what do you think about genesis (MegaDrive) emulation?

---

### Post by keyshawn on 2005-07-08
[QUOTE=Akir]Everything emulated doesn't work as well on linux as it did for me on windows. I don't know why, but if I had to guess, I'd say it's because the developers spend more time on windows because it is (unfortunately) more popular then linux. Maybe I'll get a faster computer that these will work on better. Or I'll actually spend time on compilation to speed it up instead of using packages....

By the way, what do you think about genesis (MegaDrive) emulation?[/QUOTE]

The most mature genesis emulator out there is Gens, which does have a linux port. The source is available for it and can just be built. 
Right there is a package that can be built [a .deb] for the community. 

[maybe I'll do it this weekend]

cya,
skora.

---

### Post by miscz on 2005-07-10
There is one thing that Linux fails badly. There is no Kailera - of course it's not fault of oss community but developers of Kailera who won't release Linux version. Blah.

---

### Post by Snipersnest on 2005-07-12
Kailera is what I'm looking for... I host a it on my dedicated server in NY...but I can't find anything close to it for the client side.  Sucks I'm in the hole on this too.

---

