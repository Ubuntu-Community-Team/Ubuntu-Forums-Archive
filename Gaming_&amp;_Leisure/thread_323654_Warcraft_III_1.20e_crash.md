---
title: "Warcraft III 1.20e crash"
date: 2006-12-22
forum: Gaming &amp; Leisure
---

### Post by squishywalrus on 2006-12-22
Alright, I have Warcraft III: The Frozen Throne 1.20e installed on Wine 0.9.27 on edgy 6.10 with an X800 PRO ATI card (8.31 drivers).  Now, I have it running with nocd, and everything works fine, but whenever I enter a game, about 10 seconds into the game, it locks up and I'm forced to hard reboot (this happened when I was running without the nocd as well).  Unfortunately, since I'm forced to hard reboot, I don't get the chance to see any errors that could pop up ](*,) 

Anyone have any ideas?

Thanks,
Nick

---

### Post by squishywalrus on 2006-12-24
After a bit of playing around, I've found it only happens when I'm playing Battle.net games.  If I  try just single player campaign games, everything works fine (I played through a few levels in about an hour without any hanging or crashing).  Any clues?

Thanks

---

### Post by Julas on 2007-06-02
I think I have the same problem. Actually, the system is still up but all input/output is frozen. However, I have an SSH server which allows me to login from another computer and when I kill -9 war3.exe everything gets back to normal.

I had tried various things and I managed to reduce the problem a bit. First of all, the game seems to run longer without any crash when I turn off AGP 8x. Moreover, reverting to 'ati' driver from 'fglrx' gives me some additional few minutes, so I would be even able to play a short game (~ 10-12 minutes). I guess switching off the sound makes it even longer, but playing without any sound isn't really what I'd like to end up with.

My specs:
Athlon XP 2600+
512 MB RAM
ATI Radeon 9600 Pro
Wine 0.9.38

I'm really out of ideas at this point. The log I've managed to capture doesn't seem to provide any answers:

```
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x34f64c,0x00000000), stub!
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
*********************************WARN_ONCE*********************************
File r300_vertexprog.c function valid_dst line 333
Output 3 not used by fragment program
***************************************************************************
fixme:imm:ImmGetOpenStatus (0x16f898): semi-stub
fixme:imm:ImmReleaseContext (0x10028, 0x16f898): stub
fixme:imm:ImmGetOpenStatus (0x16f898): semi-stub
fixme:imm:ImmReleaseContext (0x10028, 0x16f898): stub
fixme:imm:ImmGetOpenStatus (0x16f898): semi-stub
fixme:imm:ImmReleaseContext (0x10028, 0x16f898): stub
fixme:imm:ImmGetOpenStatus (0x16f898): semi-stub
fixme:imm:ImmReleaseContext (0x10028, 0x16f898): stub
fixme:imm:ImmGetOpenStatus (0x16f898): semi-stub
fixme:imm:ImmReleaseContext (0x10028, 0x16f898): stub
err:dsound:DSOUND_MixOne underrun on sound buffer 0x1814c0
err:dsound:DSOUND_MixOne underrun on sound buffer 0x1814c0
err:dsound:DSOUND_MixOne underrun on sound buffer 0x1814c0
err:dsound:DSOUND_MixOne underrun on sound buffer 0x1814c0
fixme:imm:ImmGetOpenStatus (0x16f898): semi-stub
fixme:imm:ImmReleaseContext (0x10028, 0x16f898): stub
fixme:imm:ImmGetOpenStatus (0x16f898): semi-stub
fixme:imm:ImmReleaseContext (0x10028, 0x16f898): stub
err:dsound:DSOUND_MixOne underrun on sound buffer 0x1814c0

[then about 2500 more 'err:dsound:DSOUND_MixOne underrun on sound buffer 0x1814c0'
```

It would seem that the sound causes the problem, but I remember trying without it and it still crashed.

---

### Post by Julas on 2007-06-02
I've just run the game through aoss and got rid of the underruns. However, the game still crashed after about 5 minutes and I got some additional errors at the beginning:

```
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x34f64c,0x00000000), stub!
err:wave:DSDB_MapBuffer Could not map sound device for direct access (No such device)
err:wave:DSDB_MapBuffer Please run winecfg, open "Audio" page and set
"Hardware Acceleration" to "Emulation".
err:wave:wodOpen fragment size set failed, size is now 4096
Your Open Sound System driver did not let us configure small enough sound fragments.
This may cause delays and other problems in audio playback with certain applications.
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
*********************************WARN_ONCE*********************************
File r300_vertexprog.c function valid_dst line 333
Output 3 not used by fragment program
***************************************************************************
fixme:imm:ImmGetOpenStatus (0x170370): semi-stub
fixme:imm:ImmReleaseContext (0x10028, 0x170370): stub
fixme:imm:ImmGetOpenStatus (0x170370): semi-stub
fixme:imm:ImmReleaseContext (0x10028, 0x170370): stub
fixme:imm:ImmGetOpenStatus (0x170370): semi-stub
fixme:imm:ImmReleaseContext (0x10028, 0x170370): stub
fixme:imm:ImmGetOpenStatus (0x170370): semi-stub
fixme:imm:ImmReleaseContext (0x10028, 0x170370): stub
```

Additionally, it seems only the screen is blocked when the games crashes. I was listening to mp3s and they kept playing when Warcraft crashed.

---

### Post by squishywalrus on 2007-06-22
yes, this is exactly the problem, I was having then.  My mp3's continue to play as well.  Anyone else have better luck?  I'd really like to be able to play this game in ubuntu :(

---

### Post by Julas on 2007-06-22
I found out it's a regression since 0.9.18:
[http://bugs.winehq.org/show_bug.cgi?id=8770](http://bugs.winehq.org/show_bug.cgi?id=8770)
Install 0.9.17, it's not perfect, but playable. And tell me if you also experience such occasional 'hiccups'/1 sec. freezes.
Oh, and I would appreciate if you voted on that bug on Wine's bugzilla.

---

