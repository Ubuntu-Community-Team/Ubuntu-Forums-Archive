---
title: "Really wacky GNOME?"
date: 2014-06-20
forum: Desktop Environments
---

### Post by alan31 on 2014-06-20
I installed Ubuntu minimal 12.04 onto my Wandboard Quad, and then installed ubuntu-desktop on top of that. The window manager seems to (mostly) work, able to pull up Firefox, GIMP, settings, and whatnot. However, the (I think it's GNOME) GUI is messed up. The top bar only extends 1440 pixels and looks squished, as if it were rendered at 1920x1080 and then resized to 1440x1080. The icons on the left are all greyed out and have odd stripes through them as well, and when using the dash, I have to move my mouse to where the icons should be rendered properly in order for it to highlight (for example, I have to click nothingness in the top-right corner of the screen to open up the power menu, which itself looks fine). Also, the terminal app seems to be black, although it does function (I had to use it to take the gnome-screenshot).

What baffles me is that, when an application is opened, the application's bar looks fine. The login screen looks perfect and gorgeous as well. The issue persists with all of the themes included by default, and in display, Ubuntu correctly recognizes the resolution as 1920x1080.

Here's my .xsession-errors:
[http://pastebin.com/R7wydrjS](http://pastebin.com/R7wydrjS)
[IMG]https://lucario.info/ubuntuscreenshot.png[/IMG]

---

### Post by kansasnoob on 2014-06-20
That's the Unity DE. Since that's 12.04 (Precise) a couple of things come to mind.

Precise offered both the Unity DE which used the Compiz window manager and Unity-2D which used the Metacity window manager as a fallback for hardware not capable of running the standard Unity session. You can see which session is running by running this command:

```
echo $DESKTOP_SESSION
```

I'm curious what graphics chip you are running? Have you checked for "Additional Drivers" in System Settings?

This command would provide graphics chip info:

```
lspci | grep VGA
```

And this should show if your hardawre is Unity capable:

```
/usr/lib/nux/unity_support_test -p
```

---

### Post by alan31 on 2014-06-20
Kansasnoob,

Thanks for your help. 
Running ```
echo $DESKTOP_SESSION
``` returns "ubuntu-2d", ```
lspci
``` returned "00:00.0 PCI bridge: Device 16c3:abcd (rev 01)" (Grep'ing for VGA returned nothing, maybe it has something to do with it being hooked up to HDMI?)

Lastly, running ```
unity-support-test
``` has this result:
```

libEGL warning: DRI2: Failed to authenticate
OpenGL vendor string:   Mesa Project
OpenGL renderer string: Software Rasterizer
OpenGL version string:  OpenGL ES 2.0 Mesa 8.0.4

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             no
GLX texture from pixmap:  no
GL npot or rect textures: no
GL OES EGL image:         no
EGL KHR image pixmap:     no
EGL version is 1.4+:      yes

Unity supported:          no

```

That sure does look like a lot of "no". Is this a graphics driver problem, then?

---

### Post by kansasnoob on 2014-06-20
I wonder if hardinfo might provide the needed info:

[https://help.ubuntu.com/community/HardInfo](https://help.ubuntu.com/community/HardInfo)

Have you checked for Additional Drivers in System Settings?

There are a lot of people smarter than I am here on the forums when it comes to graphics drivers :)

---

### Post by deadflowr on 2014-06-20
> **kansasnoob said:**
> I wonder if hardinfo might provide the needed info:

[https://help.ubuntu.com/community/HardInfo](https://help.ubuntu.com/community/HardInfo)

Have you checked for Additional Drivers in System Settings?

There are a lot of people smarter than I am here on the forums when it comes to graphics drivers :)

You should get the gist of hardinfo with
```
sudo lshw
```
if you do lshw, either pastebinit, or post it here with [code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168"), please.

---

### Post by alan31 on 2014-06-20
Just looked under Additional Drivers- it just says that no proprietary drivers are in use on this system.

After installing lshw and running "sudo lshw", it just made the next line of my terminal say "DMI" for a second before being replaced by my bash prompt. "sudo lshw > out.txt" resulted in an empty text file, too.

Thanks again,
Alan

---

### Post by deadflowr on 2014-06-20
lshw is already installed by default on Ubuntu.

Next step would be tell us what machine you have.

---

### Post by alan31 on 2014-06-20
Ah, since I installed Ubuntu-minimal and apt-get'ed ubuntu-desktop, perhaps it wasn't there. This is running on a Wandboard Quad, an i.MX6-based armv7 system.

---

