---
title: "Can I set up a screensaver? (using Ubuntu GNOME 15.10)"
date: 2015-10-24
forum: Desktop Environments
---

### Post by leon.lain.delysid on 2015-10-24
Hi all!

I have been wondering for some time… Is there a screensaver daemon and how to configure it?
I'd just like my screen to display Matrix-style images or beautiful shapes and colors or something while it's not in use. It's difficult to find that. So is there any way I can do that? Or why not?

And by the way, I have an off-topic question: do Ubuntu 15.10 or Ubuntu GNOME 15.10 still use our legacy X.org server or did we move on to Wayland or something else? Seems like screensaver applications depend on that…

Thanks for reading!

GRRRowl,
Léon

---

### Post by Frogs Hair on 2015-10-24
Gnome-screensaver controls lock and will display a static image in gnome. Screen savers on older tube monitors had purpose besides eye candy and newer flat screen monitors don't require them . Xscreensaver is available in the repository and there are instructions available with a search though I didn't find any for 15.10. There is more involved than simply installing the xscreensaver package. I tested xscreensaver once and didn't really care for the looks of what was available and I don't think the package has been updated in a long time. 


[http://askubuntu.com/questions/64086/how-can-i-change-or-install-screensavers](http://askubuntu.com/questions/64086/how-can-i-change-or-install-screensavers)

---

### Post by Dennis N on 2015-10-24
This post has some directions on installing xscreensaver packages:

[http://ubuntuforums.org/showthread.php?t=2287446&p=13324020#post13324020](http://ubuntuforums.org/showthread.php?t=2287446&p=13324020#post13324020)

you need to first install xscreensaver plus the other packages listed there.

Note: the most complex and elegant screensavers are in the package rss-glx

_xscreensaver Releases:_

Latest Release (bug fixes) by the Developer was on Oct 23, 2015. This is version 5.34
Previous Releases which had new screensavers added by the Developer were 5.31 in Nov 2014 and 5.33 in Jul 2015.

Ubuntu Repository contains 5.30 (Sep 2014 - Wily, Vivid) and 5.15 (Sep 2011 - Trusty, Precise)

---

### Post by leon.lain.delysid on 2015-10-29
Well, thanks a lot for all these explanations!
What I want these  screensavers for is just for the eye candy. Especially since I have a 4k  screen (which GNOME and GNU/Linux operate perfectly well, if that still  surprises anyone ;) ). OMG, the eye orgasm, you have no idea how  beautiful all these screensavers look on such a screen. I spent hours  looking at all of them. 4k screens are so awesome!! ^^

[FONT=courier new]xscreensaver[/FONT] indeed doesn't integrate with the GNOME lock screen though, that's just something one has to accept… Although, there is a checkbox to set it to demand the password when waking up the computer from the screensaver state.

---

### Post by Dennis N on 2015-10-29
Thanks for your feedback. I always disable any other screen locker program (sometimes these are also called "screensavers", but they don't display any) to avoid interactions between it and xscreensaver. Those include gnome screensaver and light locker.  I hope you checked out some of the rss-glx screensavers like euphoria or helios. Quite amazing.

Ubuntu MATE: Users of Mate-screensaver are able to use the same screensaver packages without installing xscreensaver - they are compatable.

---

