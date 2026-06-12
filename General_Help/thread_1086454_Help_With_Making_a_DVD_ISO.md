---
title: "Help With Making a DVD ISO"
date: 2009-03-04
forum: General Help
---

### Post by Adrenochrom3 on 2009-03-04
Hey i just copied a movie, and i want to burn it to make a copy. i have VOB, IFO, and BUP files. how do i take these files on my comp, and create an ISO to burn to DVD? 

Please and Thank you.

---

### Post by mb_webguy on 2009-03-04
If you have those files, I'm assuming they're in a VIDEO_TS folder, correct?  If that's the case, then I believe you can open Brasero, click Video Project, and drop the whole VIDEO_TS folder into the Brasero window.  Then burn the project to a DVD.

If you use k3b, from the start page click Futher Actions, then New Video DVD Project.  This will automatically give you the VIDEO_TS folder in the bottom pane, where you can drop those files.

Btw, for future reference, it's generally simpler to copy the DVD as a disc image (ISO) rather than as the VOB files.  Both Brasero and k3b provide options for this.  If you want to convert a dual-layer DVD to a single-layer DVD, you can use k9copy or dvd95.

---

### Post by Adrenochrom3 on 2009-03-04
well i just want to make sure, because i want to be able to watch it on a dvd player via the tv.  any other opinions?

---

### Post by mb_webguy on 2009-03-04
Well, if you want to be able to check before you burn, when you click to burn the disc, select to write an image instead.  This is in the drop-down list in Brasero, and in k3b you'd check the Only Create Image box on the Writing tab.

Once you have the image, you can mount it from the terminal with the following commands.```
sudo mkdir /media/iso
sudo mount -o loop /path/to/filename.iso /media/iso
```

Now you can open the image as if it were a disc.  If it works, then you can unmount the iso (with "sudo umount /media/iso"), and then burn the iso with Brasero or k3b.

---

### Post by wildman4god on 2009-03-04
I agree with this, k3b and brazareo do a pretty good job at making video dvds, they both know that your most likely wanting to use this on a dvd player, but just to make sure I will look up a toutorial and post the link.

---

### Post by wildman4god on 2009-03-04
Here you go:

[http://davestechsupport.com/blog/2009/01/03/making-a-video-dvd-in-ubuntu-linux/](http://davestechsupport.com/blog/2009/01/03/making-a-video-dvd-in-ubuntu-linux/)

This tutorial uses a program called DeVeDe to make a video dvd, and it looks pretty solid, it even has controls to customize your dvd menus.

As I said before the best way to learn this stuff is to just try it out and be willing to make some mistakes (unless the mistake could cost a significant amount of money) But blank dvd's aren't expensive so this is one area you could afford to experiment with, the forums will still be here if you need us, but I would encourage you to not be afraid to play around with ubuntu and just try stuff on your own first.

---

### Post by fooman on 2009-03-04
devede is great!  but, if you are in the united states,  make sure that NTSC is selcted ...PAL is selected by default,  so you have to make sure to change that or you will end up with a coaster for sure.

---

### Post by wildman4god on 2009-03-04
> **fooman said:**
> devede is great!  but, if you are in the united states,  make sure that NTSC is selcted ...PAL is selected by default,  so you have to make sure to change that or you will end up with a coaster for sure.

Thanks for that, I actually don't have any experiance burning video dvd's myself, I am just good at finding out how to do stuff really quickly.

---

