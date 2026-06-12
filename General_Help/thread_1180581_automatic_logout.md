---
title: "automatic logout"
date: 2009-06-07
forum: General Help
---

### Post by umairahmed on 2009-06-07
I am getting automatic logout in ubuntu 9.04. its takes 2-3 min and then i get logout without any notice.. note: i am not idle during this time

sorry ive accidentally posted the same question twice. Kindly help me remove one thread. i am new to this forum

---

### Post by woedend on 2009-06-07
> **umairahmed said:**
> I am getting automatic logout in ubuntu 9.04. its takes 2-3 min and then i get logout without any notice.. note: i am not idle during this time

sorry ive accidentally posted the same question twice. Kindly help me remove one thread. i am new to this forum

Is it actually "logging you out" or is X crashing.  That is, it is a smooth logout procedure back to the GDM(login screen)...or does the display appear to crash(black out completely abruptly) and come back up to the GDM?  Or is it rebooting completely?   The only logical reason I can think of for this happening is the display crashing.

---

### Post by colau on 2009-06-07
> **umairahmed said:**
> I am getting automatic logout in ubuntu 9.04. its takes 2-3 min and then i get logout without any notice.. note: i am not idle during this time

sorry ive accidentally posted the same question twice. Kindly help me remove one thread. i am new to this forum
Does this help?
[check]("http://ubuntuforums.org/showthread.php?t=1180428")

---

### Post by sigixv on 2009-06-07
perhaps an automatic task scheduler which autostarts at login?

---

### Post by umairahmed on 2009-06-07
> **woedend said:**
> Is it actually "logging you out" or is X crashing.  That is, it is a smooth logout procedure back to the GDM(login screen)...or does the display appear to crash(black out completely abruptly) and come back up to the GDM?  Or is it rebooting completely?   The only logical reason I can think of for this happening is the display crashing.
i dont know... it all happens so fast... all of a sudden i am presented with login window

---

### Post by gcshum on 2009-06-08
I have the same problem. I was just browsing with Firefox. And all in a sudden, I got logged out back to the login screen; not reboot but back to login in screen. If I log back in, this will happen again very soon. I ended up rebooting and all's well. This has happened several times.

---

### Post by GhostCard on 2009-06-10
I'm been trying to even log in since upgrading to 9.04. Every time I log in i am dumped back at the login screen after about 5 to 10 sec. I have tried all the brands of graphics cards i have, same result. What else can i try before going back to 8.10?

P4 2.0GHz
Savage (on-board) and Nvidia MX440 and ATi 9200 and Voodoo FX3
Only have stock 9.04 software due to the fact i can't login.

---

### Post by Buffalo Soldier on 2009-07-05
Same problem here. Stock Karmic Alpha 2 had no problem. Only after dist-upgrading I face this problem. The logout comes at random time.

---

### Post by fadumpt on 2009-10-18
Any fix to this yet?  I'm running 9.04 and when I open a song, or click on something, etc it will go black and end up at the login screen and you have to log back in and try again.

This seems to happen mostly when opening a song.

---

### Post by alfovic on 2009-12-02
it also happens to me, i have a msi wind u100 with ubuntu netbook remix 9.10 
when it hapened i saw some lines in my screen
the only word i could read was something like timidity...

---

### Post by zbyszek on 2009-12-29
Have the same problem. That's so bad, it ruins confidence that ubuntu has. I will watching for solution. Asus F3Q and ubuntu 9.04, shame on it.

---

### Post by fadumpt on 2009-12-29
I upgraded my system to 9.10 and it works great now.  For now, that might be the best solution.

---

### Post by pveurshout on 2009-12-30
For me it worked fine in Jaunty but started to happen after I installed Karmic. As far as my knowledge goes, it's definately an X crash. 

This was in dmesg:
```
[20920.389627] ACPI Warning: \_SB_.PCI0.PEGP.DGFX.MXMI: Excess arguments - needs 1, found 2 20090521 nspredef-287
[20920.389671] ACPI Warning: \_SB_.PCI0.PEGP.DGFX.MXMS: Excess arguments - needs 1, found 2 20090521 nspredef-287
```

..and this was in Xorg.0.log.old:
```
Backtrace:
0: /usr/bin/X(xorg_backtrace+0x26) [0x4f00c6]
1: /usr/bin/X(xf86SigHandler+0x41) [0x4852c1]
2: /lib/libc.so.6 [0x7f4315af3530]
3: /usr/bin/X(FindGlyphRef+0x2c) [0x5277cc]
4: /usr/bin/X(FindGlyphByHash+0x28) [0x527e38]
5: /usr/bin/X [0x534129]
6: /usr/bin/X(Dispatch+0x394) [0x44e174]
7: /usr/bin/X(main+0x3b5) [0x434085]
8: /lib/libc.so.6(__libc_start_main+0xfd) [0x7f4315adeabd]
9: /usr/bin/X [0x433509]
Saw signal 11.  Server aborting.
(II) AT Translated Set 2 keyboard: Close
(II) UnloadModule: "evdev"
(II) CKA7216: Close
(II) UnloadModule: "evdev"
(II) Sleep Button: Close
(II) UnloadModule: "evdev"
(II) Video Bus: Close
(II) UnloadModule: "evdev"
(II) Power Button: Close
(II) UnloadModule: "evdev"
(II) Macintosh mouse button emulation: Close
(II) UnloadModule: "evdev"
(II) UnloadModule: "synaptics"
(II) Microsoft Basic Optical Mouse: Close
(II) UnloadModule: "evdev"
(II) PS/2 Generic Mouse: Close
(II) UnloadModule: "evdev"
 ddxSigGiveUp: Closing log
```

Anyone know where to go from here?

---

