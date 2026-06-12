---
title: "Wine hangs the system"
date: 2006-11-02
forum: Gaming &amp; Leisure
---

### Post by Dahack on 2006-11-02
Hello

I have got this problem with wine hanging the whole system when im
playing warcraft3 in battle.net. I have tried reinstalling the game,
reinstalling wine, installing an older wine version and disabling the
sound emulators. No use - the system still hangs, but ONLY in warcraft
3 battle.net ranking games about 30 seconds after starting the game.

I'v heard that the problem might be in my own kernel (opinnions, hints,
tips?). I'v got this problem ever since i moved my computer to a LAN about
a week ago, it might had taken some physical damage on the way there, 
so could it be that something inside my computer that is broken and thats why i'v got this problem?

I would be most pleased if you could help me with this problem, since i
got a warcraft 3 tournament next month, and i really need the practise :)

(ubuntu 6.06, wine 0.9.22 [older version since the newest one doesen't work for me], Warcraft3:the Frozen Throne version 1.20e)

Thank you for reading

- Dahack

---

### Post by B0rsuk on 2006-11-02
Are you sure it's the **system** that hangs ? Did you try CTRL-ALT-F1 or CTRL-ALT-BKSP ?

---

### Post by Dahack on 2006-11-02
Yes, i am quite sure, when it hangs after a moment of starting a battle.net ladder game (only hangs in ladder games for some reason...) the screen freezes and im hearing these REALLYYY slowed down sounds of the game for a while. Then it just stays there and nothing happens what ever i do - have tried lots of key combinations but none of them seem to work. 
The only way i'v found to clear is rebooting. :-k

---

### Post by Dahack on 2006-11-03
Come on now, your telling me that no-one of you hasn't encountered this problem? 
Just give me some information, like is there something more to try to get this work before reinstalling ubuntu?
I really really need to this working, wc3 is money for me

---

### Post by ABCS_Firebird on 2006-11-15
I have the same problem. There are also some people in the german forum who got it too.

error msg is:

> fixme:cdrom:CDROM_DeviceIoControl Unsupported IOCTL 2d1400 (type=2d access=0 func=500 meth=0)
fixme:cursor:SetSystemCursor (0x111e,00007f8a),stub!
fixme:cursor:SetSystemCursor (0x1126,00007f00),stub!
fixme:cursor:SetSystemCursor (0x1136,00007f03),stub!
fixme:cursor:SetSystemCursor (0x113e,00007f01),stub!
fixme:cursor:SetSystemCursor (0x114e,00007f88),stub!
fixme:cursor:SetSystemCursor (0x115e,00007f86),stub!
fixme:cursor:SetSystemCursor (0x116e,00007f83),stub!
fixme:cursor:SetSystemCursor (0x117e,00007f85),stub!
fixme:cursor:SetSystemCursor (0x118e,00007f82),stub!
fixme:cursor:SetSystemCursor (0x119e,00007f84),stub!
fixme:cursor:SetSystemCursor (0x11ae,00007f04),stub!
fixme:cursor:SetSystemCursor (0x11be,00007f02),stub!
err:ole:CoCreateInstance apartment not initialised
fixme:advapi:SetSecurityInfo stub
fixme:win:EnumDisplayDevicesW ((null),0,0x34ed50,0x00000000), stub!
fixme:win:EnumDisplayDevicesW ((null),0,0x34ed80,0x00000000), stub!
fixme:wave:DSD_CreateSecondaryBuffer (0x190878,0x1a53144,180e0,0,0x19144c,0x19155c,0x191428): stub
fixme:sync:CreateIoCompletionPort (0xffffffff, (nil), 00000000, 00000000): stub.
fixme:imm:ImmGetOpenStatus (0x161208): semi-stub
fixme:imm:ImmReleaseContext (0x10028, 0x161208): stub
err:dsound:DSOUND_MixOne underrun on sound buffer 0x191400
fixme:imm:ImmGetOpenStatus (0x161208): semi-stub
fixme:imm:ImmReleaseContext (0x10028, 0x161208): stub
fixme:imm:ImmGetOpenStatus (0x161208): semi-stub
fixme:imm:ImmReleaseContext (0x10028, 0x161208): stub

My System:
Ubuntu 6.10, wine 0.9.25, Abit KV8 Max3, Athlon64 3200+, Radeon 9800pro, SB Live! Value, Onboard Sound: V8237

It is not the whole system which is crashing (i can hear the sound from other apps in background), but the screen is freezing and so its not possible to do anything without pushing reset or power off.

I also tried to play warcraft without sound but got the same problem there. It runs without any problems in custom or singeplayer games but in a ladder game it crashes in less than 5min.

There also seem to be some connection to the windows version settings in winecfg, but i can't determine this exactly atm.

Btw. a friend of mine runs warcraft perfectly with wine 0.9.24 and Suse 10.1 (64bit, kde).

Can please everybody who has the same problem start with

&> war3.log

Maybe there are some common msgs.

---

