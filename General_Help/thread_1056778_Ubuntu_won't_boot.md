---
title: "Ubuntu won't boot"
date: 2009-02-01
forum: General Help
---

### Post by dj9928 on 2009-02-01
I thinking i've posted about this before but have got no where, hopefully this time around I'll get somewhere.

I have posted a video of the issue [HERE]("http://uk.youtube.com/watch?v=w4l9mds8ry8"). Basically it gets so far then just stops and thats it, game over. And it doesn't matter if you install, use Wubi or run a live CD, or if you use any of the other Ubuntu based distros I.E Kubunt or Mint,

Any help appreciated

---

### Post by Yellow Pasque on 2009-02-01
It's probably a hardware/driver issue, but your video doesn't give much info. Try it again, this time without the splash screen.

---

### Post by dj9928 on 2009-02-01
And how do I do that?

---

### Post by heindsight on 2009-02-01
There could be a million reasons why it's not booting and without more info it's impossible to tell what the problem could be (that video doesn't exactly give any useful information).

Try pressing ESC when GRUB says "Press ESC to enter the menu..." then press 'e' to edit the boot command line, nest use the arrow keys to highlight the line that starts with 'kernel' press 'e' again to edit the line, and then remove the words 'quiet' and 'splash' then press Enter and then 'b' to boot.

Now, instead of a splash screen, you'll see all sorts of messages detailing what's going on during the boot process. Write down the last few messages before it gets stuck and post them here.

---

### Post by dj9928 on 2009-02-01
Right, its to do with the Atheros 5007EG Wifi card, or at least thats where it stops, however it doesn't give any error

---

