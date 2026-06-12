---
title: "after dell fixed my laptop, x.org b0rked up"
date: 2005-05-23
forum: Desktop Environments
---

### Post by simianMiscreant on 2005-05-23
My laptop wouldn't turn on, so I shipped it to Dell. A new screen, video card, and motherboard later, the problem is solved - but X won't work now! None of my settings should have changed - everything works in Windows, and all the hardware is exactly the same as what I had before. However, now when I boot Ubuntu, instead of showing me the login screen as it normally would, the screen turns a blinding shade of white, and the brightness intensifies a little more, with the left side of the screen being *seriously * bright (worryingly so). I hear the sound effects I should, and when I type my username and password and press enter I hear the normal startup noises. I can post X server output later tonight, but until then...anyone know what's going on?

video card: 256mb vram radeon 9800 mobility
display: 1920x1200
video driver: fglrx (I even had hardware acceleration...)

---

### Post by agds on 2005-05-24
Could you post the "Monitor" section of your /etc/X11/xorg.conf file?  I had a problem with my Dell desktop where it would only display in 640 x 480 @ 60 Hz, which was quite irritating.  Editing a few lines in xorg.conf cured it.  Your troubles sound more significant, but the cause could be the same.

---

