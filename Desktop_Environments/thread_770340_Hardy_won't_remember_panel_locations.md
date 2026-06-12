---
title: "Hardy won't remember panel locations"
date: 2008-04-27
forum: Desktop Environments
---

### Post by mike2357 on 2008-04-27
Since upgrading to Hardy, I've had a problem with Gnome panels moving to a different location after rebooting.  Specifically, I have two panels at the bottom of the screen, but after I reboot, their location is reversed.  Any ideas?

---

### Post by ugly_b on 2008-04-28
I have the same exact problem.  I keep 2 panels along the bottom of the screen.  But the panel with the Menus and the Clock always wants to stay on the bottom after a reboot.

I had it the same way with Gutsy and didn't have this problem.  It's obviously a bug somewhere  :(

---

### Post by mike2357 on 2008-04-29
Well, here a method that seems to work, although it's not very elegant:

1.  Log out and log back in, so the panels are in the "wrong" position.
2.  Instead of switching the positions of the panels, move all of the launchers on the top panel to the bottom one, and vice versa.  You may have to do this in stages, because probably neither panel has room for all of the launchers.
3.  Log out and log back in.

This seemed to work for me.  Good luck!

---

### Post by ilizol on 2008-05-03
It works almost always. Thank you.

---

### Post by supermelon928 on 2008-05-05
you may have tried this long ago, but it could have to do with the orientation (top, left, bottom, right) under "configure desklet".

that's the only idea i have.

---

### Post by ilizol on 2008-05-05
It works for me.

---

### Post by mizar001 on 2008-05-07
Hi all. The problem is not only in hardy. I have this problem from feisty. 

The solutions is not a real one, that's a workaround, like already said, on moving all icons of the main panel in another panel.

The problem is that sometimes (not very often though) the panel returns in the original position as if the panel with clock and menu will be re-promoted as the main panel.

A lack in the gnome panel is a possibility to 'LOCK' the panels to their positions. 

Any technical (terminal,config editor) solution ? 

Thanks.

---

### Post by Roaring Silence on 2008-05-11
I have the same problem too. There must be a configuration file in the /home/user directory, but I can't find it. Surely someone knows where it is?

---

### Post by Roaring Silence on 2008-05-16
This solution worked for me: I moved the lower panel, which I wanted on top, to the right hand edge of the screen before shutting down. Next time I booted up, the panel was still on the right hand edge of the screen. I moved it to be on top of the other panel, which was now where I wanted it on the bottom edge of the screen. After the next boot-up the panels opened in my preferred locations, and have stayed that way since.

---

