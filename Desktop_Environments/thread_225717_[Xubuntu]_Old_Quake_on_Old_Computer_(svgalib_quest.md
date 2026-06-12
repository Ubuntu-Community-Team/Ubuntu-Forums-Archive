---
title: "[Xubuntu] Old Quake on Old Computer (s/vgalib question)"
date: 2006-07-30
forum: Desktop Environments
---

### Post by Krank on 2006-07-30
Oooh, lovely. Just installed Xubuntu on a 350mhz and 256 mb RAM, and a RIVA 128... And it works. I can even run Photoshop 5.5 without much trouble...


So: What games can I get to run on this comp (my... er... tertiary comp)? Starcraft went out the window since Wine uses some weird conversion thingy through the graphics card, which needs to be very good (and RIVA 128 isn't - and I can't fit anything else into the box, since it's too cramped).

Ah! I know! Let's try Quake!

* several botched attempts at squake, quakeforge, and others later *



OK, so I can get FuhQuake up and running beautifully. Lovely.

What isn't quite as lovely is the lack of mouse. I just can't get it to work...


Some stuff that might help y'all to point me in the right direction:

* The mouse is a Microsoft Trackball Optical connected via USB.
* X11 (xorg.conf) lists the mouse device as "/dev/input/mice".

I edited the libvga.config to say:

mouse Microsoft

and

mdev /dev/input/mice


And still, it doesn't work.

Any ideas?

Is there a way to let libvga autodetect the mouse? Is there a way to test wether or not the problem is with FuhQuake or with libvga? Has anyone else out there had similar problems or experiences, or has anyone gotten fuhquake.svga to work correctly?

---

### Post by Krank on 2006-07-30
Gah... nevermind. Just found out that one can start fuhquake.svga with a /mdev parameter, which did the trick if combined with configuring libvga to think that the mouse is a PS2-type...

---

