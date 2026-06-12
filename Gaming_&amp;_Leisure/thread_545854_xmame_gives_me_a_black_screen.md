---
title: "xmame gives me a black screen"
date: 2007-09-08
forum: Gaming &amp; Leisure
---

### Post by elamericano on 2007-09-08
I'm using 6.06 with the fglrx drivers. The problem is that executing xmame makes the screen go black. Even if I only do xmame -help. The one case where it doesn't blank is if the game is working and I run it -fullscreen. Unfortunately, when I use gxmame it goes black on startup and whenever I view/change properties (for obvious reasons)

To recover I do Ctrl-Alt-F1 and then Ctrl-Alt-F7. Then a non-fullscreen game will work, or I can see whatever was output. So the darn thing works eventually, but I'd sure like to avoid the black screen. The version I am using is gxmame_0.35beta2-1_i386.deb.

Please don't suggest a different program just yet. I'd like to get xmame working.

Thanks

---

### Post by elamericano on 2007-10-02
Nobody familiar with xmame? I was hoping an xorg.conf change would solve this.

I am willing to experiment :)

---

### Post by FranMichaels on 2007-10-02
Hello.

Which ati card do you have? You could try an open driver, but it may not be very good since Dapper's xorg is older...

You could try changing "fglrx" in xorg.conf to "ati" or "radeon" and see if it helps.

Also, try alt+enter (specifically left alt I think) to go from full-screen to windowed.

---

