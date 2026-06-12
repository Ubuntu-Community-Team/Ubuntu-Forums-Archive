---
title: "Need help setting up an ATI card..."
date: 2008-02-27
forum: Desktop Effects &amp; Customization
---

### Post by diablo75 on 2008-02-27
My dad just purchased a new computer and it has an ATI card of some kind it in.  I did a glxinfo to see if it supports direct rendering and it says it does.

After installing Ubuntu, and all of the updates, I attempted to enable the driver for the video card using the Restricted Drivers Manager.  It asks me to restart the computer after checking the enable box off.

Upon restarting, a screen comes up saying something like, "Ubuntu was unable to correctly detect your video card or monitor.  Manual configuration (blah blah, he told me about it over the phone and I don't remember what it said exactly)"  I told him to hit continue.  After he's logged back into his computer, the restricted driver manager shows no check box next to the driver, hence, not enabled.

I don't have any prior experience with ATI cards, only nVidia...

Thanks for the help!

---

### Post by Yellow Pasque on 2008-02-27
What kind of computer was it? What kind of card does it have?

For the restricted driver to work, make sure the restricted repo is enabled in System -> Administration -> Software Sources
Then, press Ctrl+Alt+F1 to drop to the terminal and run this:
```
sudo apt-get install xorg-driver-fglrx
sudo aticonfig --initial -f --overlay-type=Xv
```
Reboot. If that doesn't work, the card is probably too new for the Ubuntu-supplied drivers. Use the new Catalyst drivers from ATI (on their site) and method 2 here: [http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)

---

