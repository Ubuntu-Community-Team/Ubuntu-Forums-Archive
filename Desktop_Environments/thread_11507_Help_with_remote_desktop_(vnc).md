---
title: "Help with remote desktop (vnc)"
date: 2005-01-17
forum: Desktop Environments
---

### Post by niraj on 2005-01-17
Hello, I'm new to the community and have been using Ubuntu Linux 4.10 for a few days now and everything is going smoothly. Definitely the greatest distro I've seen thus far.

I ran into a problem today. I enabled remote desktop from Computer -> Desktop Preferences -> Remote Desktop. Then I got on my Windows XP computer (on the same network) and used TightVNC to connect to my Ubuntu laptop. The VNC viewer just said "Please wait - initial screen loading...", but nothing ever showed up. When I move the mouse on the Windows machine's VNC window, however, the cursor on the Ubuntu laptop does move. So it is obviously connected and somewhat working. Then I changed the encoding to zlib (random fiddle) and instead of the please wait message, I get a garbled black and white interlaced version of my desktop. Having worked with graphics before, I had seen similar corruption when image files are viewed with the wrong color depth. So I set VNC to force 8-bit graphics, and it worked! But it looks like crap of course. I was just wondering how I could set it up so it would work with a higher setting. I also tried downloading Real VNC, but right after it connects it comes up with a message saying "setPF: not 8, 16, or 32 bpp?" and this happens no matter what I set the bpp to in the options.

I've also tried editing /etc/vnc.conf and set $depth = "24" but that had no effect. Can anyone help out?

---

### Post by Darrena on 2005-01-17
You may want to try NoMachine's solution, there is a walkthrough on installing it on the HOWTO/FAQ board.

---

### Post by niraj on 2005-01-18
I'd like to use VNC if possible, since many other computers I have access to outside home have VNC installed but no support for NX.

---

