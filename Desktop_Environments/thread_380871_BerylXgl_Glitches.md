---
title: "Beryl/Xgl Glitches"
date: 2007-03-10
forum: Desktop Environments
---

### Post by novavon on 2007-03-10
Referred to [[SIZE="5"]**Install Beryl on Ubuntu Edgy**[/SIZE]]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL").
Downloaded and installed graphics card driver, beryl, and xgl.
I've provided screen shots of the problems

**Problems:**
Unable to load window borders.
The console goes white when it's turned on.
Still couldn't see the window border nor the console, after turning off the beryl-manager.
After several tries, nothing happens after turning on beryl-manager. But the whole screen turns white when I do, "beryl-xgl" command, I have to restart X in that case..


I would appreciate any comments regarding these issues.

Here is an output when I run, "beryl-manager" command.

```

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Relaunching beryl with __GL_YIELD="NOTHING"


```

---

### Post by iammeagain on 2007-03-10
I have had the same problems whenever attempting to use beryl, and not just on Ubuntu, on any other distro i could get it running on also.

 I dont remember anything i did or didn't do because that was like a month ago. Earlier i couldnt find anyone with the same problem. But if anyone can find a fix for this that would be awesome.

Oh, and my video card is a ATI Radeon 9250, or something around there. Also its PCI, cuz my stupid motherboard only came with PCI slots.

---

### Post by herbster on 2007-03-11
What version of Beryl are you using? I ran into similar problems, particularly the white screen. I would highly recommend this thread, if it doesn't solve your problem(s) with Beryl I'd be surprised:

[http://forum.beryl-project.org/viewtopic.php?f=36&t=4046](http://forum.beryl-project.org/viewtopic.php?f=36&t=4046)

---

