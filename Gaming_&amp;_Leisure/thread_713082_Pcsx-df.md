---
title: "Pcsx-df"
date: 2008-03-02
forum: Gaming &amp; Leisure
---

### Post by XSP on 2008-03-02
It appears that the PCSX project has been revived and has the x86, x86_64, and ppc users in mind.

[PCSX-DF]("http://aboenterprises.ca/pcsx-df/") is a GNU/Linux fork of the discontinued PlayStation emulator "PCSX". It currently has support (including dynamic recompilers) for x86, x86_64, and ppc32 CPUs. It comes with the necessary plugins to get up and running.

It's been around for awhile apparently, but the latest release being January 24th of this year. It's nice to see some open source work being put in to PSX emulation again. I love pSX, and it's still more compatible than this is, but this has some awesome potential.

---

### Post by acoustibop on 2008-03-02
Interesting, but inevitably it will remain a plugin-based emulator, a system that has now been shown to be seriously flawed with the emergence of the newer pluginless emulators (pSX, of course, and Xebra in Windows).

I remember even when I tried the first release of pSX, over 2 years ago now, and in Windows-only then, I was immediately struck by how superior it was to the then dominant plugin-based emulators - at that point, I'd been using ePSXe for 6 years or more, and some others for games that ePSXe couldn't play.  By the issue of about version 1.6, I knew I'd never really want to use a plugin-based emulator again

I don't think that, at this late stage, plugin-based emulators are going to recover their position in the emulation scene: there's too much inherently wrong with the plugin system.  But, it remains to be seen.

---

### Post by XSP on 2008-03-02
With the recent revival of Mupen64 and the continued development of PCSX2, both which are plugin based, it makes you wonder if this is a trend that is coming back in to style. Not to mention Ideas, the DS emulator.

I am in agreement with you however. Although I suppose that plugin based emulators allowed for more variety, I always thought of it as a rather lazy way of doing things, which I am not putting off on this persons work. He is simply trying to play catch up and not reinvent the project which is more of a task than most people would think. Picking up someones code is rarely easy.

---

### Post by acoustibop on 2008-03-02
I think the reason that Mupen64 and PCSX2 are plugin-based are partly simply because that's how they were made, and also to allow access to the hardware capabilities of things like videocards.

pSX has demonstrated, however, that emulation in software can actually work better.  pSX Author is also working on Playstation 2 emulation for pSX - this may take a while, although apparently a couple of games are running already - but I wouldn't mind betting that when it happens, it'll be far less resource intensive and work better than, say, PCSX2.

---

### Post by frenchn00b on 2008-03-02
> **XSP said:**
> It appears that the PCSX project has been revived and has the x86, x86_64, and ppc users in mind.

[PCSX-DF]("http://aboenterprises.ca/pcsx-df/") is a GNU/Linux fork of the discontinued PlayStation emulator "PCSX". It currently has support (including dynamic recompilers) for x86, x86_64, and ppc32 CPUs. It comes with the necessary plugins to get up and running.

It's been around for awhile apparently, but the latest release being January 24th of this year. It's nice to see some open source work being put in to PSX emulation again. I love pSX, and it's still more compatible than this is, but this has some awesome potential.

I hope that one day, the pcsx will be as good and as much stable as zsnes or nes emulators for linux 

still some time

---

### Post by disturbedite on 2008-03-02
i have to agree with acoustibop.  to put my opinion simply, in my experience pSX is faster than the other playstation emulators.  i simply prefer pluginless emulators.  they are less hassle too.

---

### Post by nerdy_girlscout on 2008-08-06
I don't know where I stand when it comes to plugins. Plugins allow much flexibility. If there's a part of the emulation that is bad, switch plugin. I wonder if it's really needed though to have 5 different plugins that do pretty much the same thing, when all development could be focused on one core for that emulation instead.

But one thing that is lacking in both pSX and Xebra is enhancements. In particular, neither supports enhancements of polygons (used in 3d graphics). Maybe the emulator should have a single core, but allow plugins to do all kind of enhancements (As far as I know, plugin-based emulators have the plugins do All emulation of GPU/SPU/Whatever). But I am not a developer, I know too little.

No matter which choice is the best though, I really hope we get more development on free open source emulators for GNU/Linux. pcsx-df is the only one we have in development, and it seems to go a little slow.

---

### Post by FranMichaels on 2008-08-06
> **XSP said:**
> It appears that the PCSX project has been revived and has the x86, x86_64, and ppc users in mind.

[PCSX-DF]("http://aboenterprises.ca/pcsx-df/") is a GNU/Linux fork of the discontinued PlayStation emulator "PCSX". It currently has support (including dynamic recompilers) for x86, x86_64, and ppc32 CPUs. It comes with the necessary plugins to get up and running.

It's been around for awhile apparently, but the latest release being January 24th of this year. It's nice to see some open source work being put in to PSX emulation again. I love pSX, and it's still more compatible than this is, but this has some awesome potential.

Thank you. I've been using pcsx-df since version 1.7 came out. It's really a matter of it being future proof. As someone who's been into the emulation scene for a long while. Closed source emulators have serious draw backs. 

They may just get abandoned and that's it. Or they may go commercial (as with Virtual Super Magicom, if memory serves...). 

The most annoying thing though, is the compatibility, instead of sharing the features, it is just a silly contest, eventually these consoles won't be available in several decades. 

So for the sake of accurate emulation, and multi-platform "future-proofness", I give pcsx-df the chance. It runs what I've used on it with no problems, and as for the plugins...

```
sudo apt-get install pcsx-df
```

Real hard right? Ubuntu has pcsx-df, it comes with basic plugins all set, and can run many games with it's built in HLE bios.

/rant

Also, the site moved.

[http://pcsx-df.game-host.org/pcsx-df/](http://pcsx-df.game-host.org/pcsx-df/)

The page where there will be official releases eventually.

[http://pcsx-df.sourceforge.net/](http://pcsx-df.sourceforge.net/)

Considering there isn't a fixed release yet, I'd say what we have isn't so bad at the moment...

---

