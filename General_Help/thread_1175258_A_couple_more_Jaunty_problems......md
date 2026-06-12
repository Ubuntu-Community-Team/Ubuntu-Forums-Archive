---
title: "A couple more Jaunty problems....."
date: 2009-05-31
forum: General Help
---

### Post by adam.ec on 2009-05-31
I've noticed that I seem to be suffering a couple more problems since installing Jaunty a week ago.

I have an Intel D945GN motherboard which I thought was going to give me some real hassle but everything seemed to install without a problem. Videos play smoothly, Flash works (after one reinstallation) sound is louder than ever and no system freezes. System boots in about 28 seconds.

However, now I've got round to using it a little more I do have one or two glitches in the machine.

First off, when using Gimp I always get big rectangular blocks of white covering up parts of layers I'm trying to work with. They disappear if I minimize the window and reopen it. Unfortunately the reappear the very second I try to use another tool. Also in Gimp, option windows and alerts do not open in a window large enough for the content and sometimes won't resize.

Secondly, when I create new folders on the desktop, or try and drag and drop to the desktop the folders or items don't appear. If I check in the terminal or in Nautilus in the Desktop directory they are there but graphically, they don't appear on the desktop until some unknown (still can't work out yet what) event occurs and then they suddenly appear.

Lastly, alert boxes with long strings of text in sometimes don't word-wrap properly and text disappears of the right hand side of the box. This is similar to the Gimp problem.

Not sure what is happening here but can someone confirm if this is related to the Intel driver problems with Xorg? Is anyone else having the same problems occuring?

I've tried to correct the Intel 945 graphic problems with the solutions on the 9.04 release notes but it appears I don't have an xorg.conf file with anything in it.

Thank you for your input.

---

### Post by 123456789123456789123456 on 2009-05-31
that is strange
Are you using a Intel Graphics driver for ubuntu, or just a generic driver provided by Ubuntu, my first thought, with the gimp problem would be a driver that is not 100% compatable with the video card.  The folder problem could be related to graphics, however the text problem, I don't see how that would be related to graphics.
xorg.conf, should deffinatly have information in it.  It should have data on the monitor, if nothing else, should read unknown.
If xorg.conf, does not have anything in it, it would appear to be a bad install, unknown as to why that would be, Intel seems to be fairly good supported by Ubuntu.
If you know the exact data that is needed in the xorg.conf file, you may be able to recreate the data in it manually.  I don't know of a way to repair xorg without reinstalling the system.  Hold on though, someone may have an idea.

---

