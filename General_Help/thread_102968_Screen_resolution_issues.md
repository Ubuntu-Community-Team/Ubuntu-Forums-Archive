---
title: "Screen resolution issues"
date: 2005-12-13
forum: General Help
---

### Post by jtball on 2005-12-13
I have tried a lot of researching to solve this problem, and have got to finally admit that this one has me stumped.

I have loaded 5.10 onto an IBM Thinkpad (1161) and everything went sweetly on install, came to GDM login screen, no problems. Image is right to edge of screen, looks to be about 800x640 resolution, very clear (and stylish, love the browns). But after logging in, the next image (which I assume to be the desktop) is blurred and smaller, to describe it as best I can. There is a big black border around the image (about an inch and a half on a 12 inch screen), and the image itself looks as though it is repeated a couple of times, each time offset to the right by another quarter of the image. Can't make head or tail of writing or icons on screen, there are 4 blurred mouse pointers, and the operation of GNU/Linux seems to continue untroubled (right-click, windows popping up, blurred of course).

I have searched quite a lot, and I haven't found a working solution (unless I have misunderstood some of them) to my problem. I guess my first question would be, why is the login screen fine, but the desktop stuffed up? Any takers?

---

### Post by jtball on 2005-12-13
A little more info...
When I boot from a knoppix live cd, there is no problem with screen resolution. I have tried altering my xorg.conf file to use the working values from the knoppix system, but it does not appear to change anything.

---

### Post by jvictor on 2005-12-13
I am not a laptop user.. So if u fry ur thinkpad I'm not gng to pay :-) Coming to the point , I may guess that it has something to do with ur Horizontal & vertical frequencies. Do u have any tech specs of the LCD monitor. look at that and try adjusting the values. and change the driver to vesa, also b4 u cahge anything can u post ur X's log ? That may give some leads.. Can u also attach those workign / non working xorg conf files ?

---

### Post by jtball on 2005-12-13
Thanks for the reply, jvictor. I tried a new tact before I saw your reply. I removed the lines specifying the frequencies, and now the login screen has the black border too, but at least the desktop does not have the "blurry" effects any more.

The screen resolution, from within gnome, is stated as 640x480. There are no other choices. I will be home soon, and I will post the xorg.conf and log files from the latptop.

The Thinkpad is a 1200 series 1161-41M. I've looked high and low, but cannot find any tech specs defining the monitor frequencies. Like I said beofre, I tried using values successful for the Knoppix live cd, but they didn't change anything.

Possibly important note: I don't have a modeline in my xorg.conf, mainly because I don't know if I can just pull a line of numbers out of my hat that will work.

---

### Post by jtball on 2005-12-13
OK, finally found my answer. And i guess its its been under my nose the whole time... in this forum!!

[]("http://http://ubuntuforums.org/archive/index.php/t-27568.html")

The key part is the conf values:

> Section "Monitor"
Identifier "Generic Monitor"
VendorName "IBM"
ModelName "SVGA 800X600@60HZ"
HorizSync 31.5-40
VertRefresh 58-62
Modeline "640x480" 25.79 640 656 720 832 480 480 484 501
Modeline "800x600" 40.35 800 816 928 1040 600 600 606 626
EndSection

Don't know where these figures came from, but they work for me. There are also further links in the page linked above that explain how to get 1024x768, but it is virtual, and I don't really want that. Hope this helps someone else, and thanks for the interest jvictor.

---

### Post by RAOF on 2005-12-13
If you have an intel integrated graphics chip, you might want to check out 855resolution.  Aparently, some of the intel chips fail to correctly report what resolutions are available, and this fixes it.

Check out the [Super Xorg Resolution Changing Thread]("http://www.ubuntuforums.org/showthread.php?t=83973&highlight=xorg+resolution")

---

