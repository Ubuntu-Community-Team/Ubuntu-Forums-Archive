---
title: "Rotation And General Display/XRANDR Properties Indicator Applet"
date: 2010-06-11
forum: Desktop Environments
---

### Post by roadkillbunny on 2010-06-11
Hello,

Some time ago, I've written a deamon for my tablet PC (ThinkPad X61) that, when the screen is in tablet mode, monitors the orientation of the tablet via the hard-drive accelerometer and rotates the display correspondingly.

You can find more information about the project here:
[http://www.krizka.net/projects/autorotate/](http://www.krizka.net/projects/autorotate/)

The deamon registers a DBUS interface, so I can control it. For example, sometimes I might want to disable the automatic rotation (when I move the laptop around a lot) or manually set the rotation of the screen. Currently I do the control using a command line scrip that I've mapped to one of the hardware buttons on the screen.

After using it for a few months, I think it would be a good idea to create a GUI to control the daemon. My current idea is to create an indicator menu that only becomes visible when the screen is in tablet mode. Then clicking the menu would show the following list of menu options:
```

Screen Rotation
 [ ] 0 degrees
 [ ] 90 degrees
 [ ] 180 degrees
 [ ] 270 degress
 [ ] Automatic

```

Here are my questions to the Ubuntu forum members:
1) What do you think of such a project? Do you have any suggestions how it could be improved?

2) Is anyone working on a similar project? I would consider writing an indicator applet for general display properties as similar. I just don't want to duplicate any work. I found the following blueprint on Launchpad about a proposed indicator applet for display properties, with support for third party applications:
[https://blueprints.launchpad.net/indicator-applet/+spec/indicator-display](https://blueprints.launchpad.net/indicator-applet/+spec/indicator-display)
However it does not seem to have received much attention yet...

---

### Post by Favux on 2010-06-11
Hi roadkillbunny,

Sounds like a good project to me, well worth doing.

I don't know if these would hold any interest for you:

[Magick Rotation]("http://ubuntuforums.org/showpost.php?p=9394701&postcount=484")

[AutoRotateDisplay]("http://github.com/pieleric/AutoRotateDisplay")

---

### Post by roadkillbunny on 2010-06-12
> **Favux said:**
> 
I don't know if these would hold any interest for you:

[Magick Rotation]("http://ubuntuforums.org/showpost.php?p=9394701&postcount=484")

[AutoRotateDisplay]("http://github.com/pieleric/AutoRotateDisplay")

Interesting scripts. They work with other laptops too, while mine only works with ones with the hdaps module for hard-drive accelerometer for now. But they can't be controller via DBus. :(

I'll contact the authors though to see if they are interested in implementing it in the future.

---

