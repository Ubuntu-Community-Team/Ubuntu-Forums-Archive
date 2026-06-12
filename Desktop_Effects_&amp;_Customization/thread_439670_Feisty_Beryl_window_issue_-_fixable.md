---
title: "Feisty Beryl window issue - fixable?"
date: 2007-05-10
forum: Desktop Effects &amp; Customization
---

### Post by HeyItsMatt on 2007-05-10
Hey guys!  I tried to get Desktop Effects and Compiz to work on Feisty, and the wobbly windows were fine, but for some reason after an initial successful cube-workspace viewing, my workspaces kept going down to 1 when effects were enabled.  So, now I am trying Beryl out with an ATI Radeon 9500 Pro / AIGLX / open source driver.  Beryl seems to be very promising - I can view the desktop cube, change desktops, see translucent title bars, use F9 to see the Expose-style window zoom-out where I choose / close a window I want, and wobbly windows work.  

However, one problem makes it unusable - when I move most windows (ex: Firefox, Gedit, Terminal) the window content seems to scramble up, resembling a static TV screen or something.  Not all programs do this, some seem to work fine (ex: VLC, GAIM).  This hasn't seemed to crash anything yet, just makes viewing window content impossible.  I've heard about a "white window" problem but I don't know if that's the same thing as what is happening to me.  Anyone know how this could be fixed?  I almost feel like maybe there's some setting related to text-rendering that I just need to turn off or something.

I followed this guide to install Beryl (had no issues, xorg.conf had what was needed in the guide)l: [http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)

Here's some specs / useful info if needed:

lspci:
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon R300 NE [Radeon 9500 Pro]
01:00.1 Display controller: ATI Technologies Inc Radeon R300 [Radeon 9500 Pro] (Secondary)

glxinfo:
direct rendering: Yes

glxinfo | grep "GLX version":  (I'm a bit of a newb, just putting down what looks important)
GLX version: 1.2 
client glx version string: 1.4
OpenGL version string: 1.3 Mesa 6.5.2

Here is the output in the command line when I choose "Beryl" from the "Select Window Manager" setting of the Beryl Manager:

```
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (2048x2048)

Reloading options
X connection to :0.0 broken (explicit kill or server shutdown).
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"
```

I think the "reloading options" at the bottom is when I flip it back to Metacity from Beryl.  Not sure though, since trying to view the terminal with Beryl enabled = scrambled stuff.

Thanks so much for any help!  This is like torture - Beryl doesn't work enough to be useable, but it works enough to tease me with its totally amazing features :)

---

### Post by blackened on 2007-05-11
In Beryl Manager, have you tried diabling the Move Window effect under Window Management?

---

### Post by HeyItsMatt on 2007-05-11
Yeah, when I disable it I still get the weird static content effect, but the windows themselves cannot be moved anywhere (they stay wherever they were when Beryl was turned on).

---

### Post by blackened on 2007-05-11
I apologize, I'm an idiot and should have thought of that. Have you adjusted any of the "Advanced Beryl Options" in the Beryl Manager context menu?

---

### Post by HeyItsMatt on 2007-05-11
> **blackened said:**
> I apologize, I'm an idiot and should have thought of that. Have you adjusted any of the "Advanced Beryl Options" in the Beryl Manager context menu?

Yeah, I changed the options that were listed in the guide that I gave a link to (changed: rendering path = copy, rendering platform = force AIGLX).  Here's the options right now:
rendering path: copy
composite overlay window: automatic
rendering platform: force AIGLX
binding: automatic
rendering: automatic

I've also tried disabled some of the effects in Beryl Settings Manager (disabling "opacity" under Accessibility and "animations" under Visual Effects didn't fix anything, neither did disabling "fade to desktop" under Desktop).

*****EDIT******

Uh, I just changed the "rendering path" option under advanced settings from "copy" to "automatic" and it looks like I am not having the problem anymore - I've been opening several programs and they all seem to look fine.  I don't know why I didn't try this before... although I don't really even know what this option means.  I wonder why this would be causing the problem?

And thanks for asking about the settings, otherwise I'm sure I never would have thought of changing that! :)

---

