---
title: "vcd or dvd slideshow"
date: 2005-12-25
forum: Desktop Environments
---

### Post by irish rebel on 2005-12-25
Guys I at wits end here , tried digikam gives me errors about imagemagick yet it is installed, tried qdvd slideshow will not work it creates the audio ts and video ts folders  but thats it crashes out or just hangs for hours .I set up picassa2 thru wine but it gave me a cannot read crrom error dvd shrink does work fine for me in wine.
I need a good dvd slideshow program so that I can add music and pictures together.

---

### Post by zoiks on 2005-12-25
If you go to the tovid website

[http://tovid.berlios.de/en/tovid.html](http://tovid.berlios.de/en/tovid.html)

and click on Manual|makeslides, it seems to have this capability somewhat (though it says (s)vcds, as opposed to dvds explicitly).

In case you are interested in doing it "the hard way", if you go to this site

[http://www.mythtv.info/moin.cgi/DvdMenuHowTo](http://www.mythtv.info/moin.cgi/DvdMenuHowTo)

It talks about creating dvd video from photos.  The context is making the videos for DVD menus, but it applies more generally since it's dvd-compliant video.  As an example, you can create a basic video stream with something like this

jpeg2yuv -n 50 -I p -f 29.97 -j menu.jpg | mpeg2enc -n n -f 8 -o menu.m2v

Then create your audio stream as a .mp2 audio file, and then remultiplex them

mplex -f 8 -o menu.mpg menu.m2v menu.mp2

The result is an mpg(2) file that can be burned to a dvd using dvdauthor and growisofs.

---

