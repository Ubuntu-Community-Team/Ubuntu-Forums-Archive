---
title: "strange lockups in fceu"
date: 2009-07-31
forum: Gaming &amp; Leisure
---

### Post by lytithwyn on 2009-07-31
I had been using fceu a lot on Intrepid to play Legend of Zelda (yes, I own the cart.)  Just recently, I installed a fresh copy of Jaunty.  Ever since then, I get random lockups in fceu where it will drop out of full screen, ignore keystrokes, but the game will continue to run.  Usually I can Ctrl+C in the console and it will quit, but sometimes even that won't kill it.

No errors are output in the console, but I'll paste the console output at the end anyway just in case.

Any ideas?  I installed directly from the Ubuntu repos.  Do you think I should try building from source?  I see the fceu project had been dropped and a new one (fceux) has been started.  Anyone have experience with it?  It's not in the standard ubuntu repos.


Starting FCE Ultra 0.98.12...
Loading ./roms/Legend of Zelda, The (GC).nes...

 PRG ROM:    8 x 16KiB
 CHR ROM:    0 x  8KiB
 ROM CRC32:  0x46e0d37d
 ROM MD5:  0x5f37d85ba0f296bd471cd674d63cb640
 Mapper:  1
 Mirroring: Vertical
 Battery-backed.

Initializing video... Video Mode: 640 x 480 x 8 bpp full screen

Initializing sound...
 Bits: 16
 Rate: 48000
 Channels: 1
 Byte order: CPU Native
 Buffer size: 1152 sample frames(24.000000 ms)

---

### Post by Grishka on 2009-07-31
disable compiz when you play.

---

### Post by lytithwyn on 2009-08-03
Ah, it didn't even occur to me that I wasn't using compiz before.  Thanks for the tip!  I even found a nice script to do it automatically here: [http://ubuntuforums.org/showthread.php?t=588497]("http://ubuntuforums.org/showthread.php?t=588497")

---

### Post by xjgnsdof on 2009-08-14
Disabling Compiz didn't work for me, though I get a different lockup than you do. On my laptop, where I run Metacity as my window manager, the sound and video stop, and keypresses don't register. I have to do a hard restart. It made no difference whether OpenGL was enabled or whether I play in fullscreen mode or windowed mode.

---

### Post by lytithwyn on 2009-08-15
Sadly, I haven't had a chance to play much since I was given the advice.  We've actually been busy at work. :P  The bit of time I have played, though, has been problem free.

It does sound like you're having a different problem.  For me, the sound and video continued like nothing had happened.

Does anyone know if Ubuntu is going to drop fceu for fceux?

---

