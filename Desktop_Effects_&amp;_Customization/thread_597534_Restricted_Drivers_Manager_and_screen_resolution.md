---
title: "Restricted Drivers Manager and screen resolution"
date: 2007-10-30
forum: Desktop Effects &amp; Customization
---

### Post by Calegero on 2007-10-30
Hi,

I just installed the gibbon in his cage, but having some troubles with Restricted Drivers Manager and my screen resolution...
When i enables my NVIDIA driver, my screen resolution becomes 1024x768, i reckon, but what i want, is to have it at 1280x1024 pixels... My screen is not on the list of screens (in Screens and Graphics) so i chose Generic, and the chose the model LCD 1280x1024 and sat resolution to 1280x1024 at 60Hz. Now you would think, it would run like a charm, but what happened was, that when i restarted my machine, Ubuntu was in 1280x1024 and looked perfect, until i opened Firefox. The window border (as in the border which holds the exit button and yes, the border:P) was gone,  and there was no desktop effects enabled. And that repeated itself with every application i started, except the console, that's just a white square which can do ****.
Currently, the NVIDIA driver is disabled, and i have no desktop effects, but it works. Now i would like to know what i've done wrong, and what i should do to make it work.
Please help

Thanks:)

---

### Post by fazavon on 2007-10-30
Try this

System > Preferences > Sessions

You will see a box of things that start up every time you login.

What you need to do next is click add

Name it Compiz
Command = compiz --replace
Comment = is optional

hit ok

reenable your Nidia drivers and reboot

that should fix it.

Let me know how it goes

//j

---

### Post by Calegero on 2007-10-30
Unfortunately it didn't quite work. The desktop effects works great now, but i still don't have no borders in the applications. You can see for yourself:

[http://img75.imageshack.us/my.php?image=scr0em4.jpg]("http://img75.imageshack.us/my.php?image=scr0em4.jpg")

---

### Post by fazavon on 2007-10-30
try installing Emerald

apt-get install Emerald

or find it in Synapic

---

### Post by Calegero on 2007-10-30
No, that didn't help either ... but maybe i have misunderstood you; should i do anything with Emerald after the installation?

---

### Post by Zorael on 2007-10-30
Emerald needs to be launched as well. Compiz does it automatically if you have the Window Decoration plugin added, I believe. Just make sure the Command field says 'emerald --replace'.

```
zorael@azrael:~$ cat /usr/bin/compiz.start
#!/bin/bash

__GL_YIELD="NOTHING" compiz --loose-binding --ignore-desktop-hints --replace ccp &
```

That's what I use to start it, by the way. Loose bindings improve performance on Nvidia cards, I hear, and Ignore Desktop Hints helps KDE and Compiz play nice(r) when it comes to viewports/desktops/workspaces. And the yield nothing part is also supposed to help. Hell if I know.

---

### Post by Calegero on 2007-10-30
I'm not sure i follow you further than to add "emerald --replace" to my 'compiz --replace' command... Well, i've done that, but that did not work either - no borders for me:/

---

### Post by Calegero on 2007-10-30
Just found [this]("http://ubuntuforums.org/showthread.php?t=596875") thread ... dunno if it's anything but, what do you think?

---

### Post by Zorael on 2007-10-30
1) Add the following to the Screen section of your xorg.conf file, for good measure (but may not be needed):
```
    Option         "AllowGLXWithComposite" "True"
    Option         "AddARGBGLXVisuals" "True"

```

2) Restart X.

3) Once logged in, open up a terminal and do:
```
$ compiz --replace &
$ emerald --replace &
```
and don't forget the ampersands.

If borders don't appear after the emerald line, something else is acting up.

---

### Post by Zorael on 2007-10-30
If it's new drivers you want, I whole-heartedly recommend Envy. It'll download and install it for you.

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

If it complains about missing dependencies, just do 'sudo apt-get install -f'.

edit: And if you're missing resolutions, you may have to add them yourself, in the same Screen section.

```
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1400x900" "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
```

---

### Post by Calegero on 2007-10-30
After installing a driver through Envy, it works! I got border and everything, except for the ability to move the windows. They just seem to be stuck in the top left corner, and even by right-clicking in the taskbar and choose move, dosn't work:/

---

### Post by Zorael on 2007-10-30
Open the CompizConfig Settings Manager, scroll way down, and enable the Move Window plugin. :>

---

### Post by Calegero on 2007-10-30
Thank you so much!!
Everything works great now - thank you!

---

