---
title: "Guild Wars Crash"
date: 2007-05-07
forum: Gaming &amp; Leisure
---

### Post by lordhebe on 2007-05-07
After getting Guild wars working with wine 0.9.36, I started working on a new character for my friends guild, we're all getting to level 10 in pre-searing Ascalon first. Well I'm lvl 6 ATM but whenever I enter the catacombs (be it from Ashford abbey or Green Hill country) the game freezes upon loading and locks my entire system, I then have to kill manually from console. The rest of the game works with very few problems. (performance issues, visual glitches, sound issues etc) but apart from this problem is perfectly playable.  I'm running the game in DirectX 8 mode, with the -noshaders -dx8 -dsound flags.

My specs are:

AMD Athlon 64 3000+
ATI Radeon X1600 Pro Drivers 8.36.5
KingMax ram 512MB DDR X2
Ubuntu Feisty 32 bit (Using metacity, not beryl)

I ran it in a terminal and this is it's output: ```
fixme:dbghelp:SymInitializeW what to do ??

```
This then repeats over and over and never stops.

---

### Post by dorath on 2007-05-07
Try starting the game with the -repair option, then zoning into the catacombs.  

-repair fixed an issue I had where the game would lockup annoyingly often in certain zones.  When I first zoned in after starting the game with -repair, a number of files were decompressed and I never had the lockups again.

---

### Post by chek2fire on 2007-05-08
run the game with windows 2000 setting and alsa in audio.then run it with -dsound like this
 wine "C:\\Program Files\\Guild Wars\\Gw.exe" -dsound

---

### Post by lordhebe on 2007-05-08
Thanks I will give that a try.

> **chek2fire said:**
> run the game with windows 2000 setting and alsa in audio.then run it with -dsound like this
 wine "C:\\Program Files\\Guild Wars\\Gw.exe" -dsound

That's what I do.


EDIT: Nah it didn't work, am trying a complete re-install, just thought, would applying the lights patch help? ([http://eurus103.googlepages.com/lights-0.9.33.patch]("http://eurus103.googlepages.com/lights-0.9.33.patch")) Will give it a try this weekend.

EDIT: It worked! Applying the lights patch worked!

---

### Post by carbonrodney on 2007-05-24
How did you get it running in the first place? It just crashes for me (works fine in Windows).

I'm running Feisty and wine v0.9.37

---

### Post by sinaen on 2007-05-25
hmm i have much problems with getting my gw to work. now i get it to wor. with -nosound options. but i have a very slooooow fps. do you know what thats all about. ive checked my xorgfile and it seems to be correct. and i have gl and direct support in x

---

### Post by Megatog615 on 2007-05-25
Do you get "Too Many Concurrently Active Lights" in the debug output? This is a bug in Wine and hasn't been fixed yet. It tends to cause the "what to do?" messages.
Please make a reply in [this](http://bugs.winehq.org/show_bug.cgi?id=7965) bug report confirming the error(if you get the above error).

Also, please upgrade to 0.9.37.

---

### Post by sinaen on 2007-05-26
nope i get this message 

fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x10e00d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x10e00d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x10e00d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x10e00d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x10e00d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x10e00d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x10e00d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x10e00d0) : stub
fixme:d3d:IWineD3DDeviceImpl_EvictManagedResources (0x10e00d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x10e00d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x10e00d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x10e00d0) : stub
*********************************WARN_ONCE*********************************
File r300_vertexprog.c function valid_dst line 333
Output 3 not used by fragment program
***************************************************************************
*********************************WARN_ONCE*********************************
File r300_render.c function r300Fallback line 424
Software fallback:ctx->Multisample.Enabled
***************************************************************************
Try R300_SPAN_DISABLE_LOCKING env var if this hangs.
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x10e00d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x10e00d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x10e00d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x10e00d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x10e00d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x10e00d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x10e00d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x10e00d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x10e00d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x10e00d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x10e00d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x10e00d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x10e00d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x10e00d0) : stub
fixme:d3d:IWineD3DDeviceImpl_ValidateDevice (0x10e00d0) : stub

---

### Post by carbonrodney on 2007-05-27
I got it working by, in the sound options of winecfg, disabling ALSA and enabling OSS.

It runs, but it is so incredibly slowly (works perfect in Windows so it's not that my hardware is ****) that it is not worth playing. 
Anyone know how to optimize it? (I am using -noshaders -dx8 -dsound flags)

---

