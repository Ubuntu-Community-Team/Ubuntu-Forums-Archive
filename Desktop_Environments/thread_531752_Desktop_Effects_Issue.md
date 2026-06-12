---
title: "Desktop Effects Issue"
date: 2007-08-21
forum: Desktop Environments
---

### Post by kh1116 on 2007-08-21
Heres the story, I tried to install compiz-fusion with my Radeon 9000.  It didnt work, so I removed it and downloaded (i think) all of the packages required for desktop effects. Now when I try to enable desktop effects, I get a message saying "desktop effects could not be enabled". I had it running before I tried to install compiz fusion. Heres the terminal output when i try to enable desktop effects:```
kevin@kevin-desktop:~$ desktop-effects
modinfo: could not find module fglrx
nvidia hardware not available

```

then when I click enable ```
gtk-window-decorator: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.
Fatal: Failed test: texture_from_pixmap support
Checks indicate that it's impossible to start compiz on your system.
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

any help greatly appreciated, thanks kevin

---

### Post by Ek0nomik on 2007-08-21
What video drives are you using?

You can try to replace your current window decorations by doing:

Alt+F2:  compiz --replace

---

### Post by kh1116 on 2007-08-21
i tried what you said, but got the same results. i have a feeling its with the xorg.conf file, but i want confirmation that it is before i edit it- ive had some problems when i edit xorg

---

### Post by Ek0nomik on 2007-08-21
> **kh1116 said:**
> i tried what you said, but got the same results. i have a feeling its with the xorg.conf file, but i want confirmation that it is before i edit it- ive had some problems when i edit xorg

Don't worry about having to edit your xorg.conf file, we can just create a backup.  :)

What video card drivers are you using?  fglrx?

---

### Post by kh1116 on 2007-08-21
ati i believe, is there a way to check?

---

### Post by Ek0nomik on 2007-08-21
> **kh1116 said:**
> ati i believe, is there a way to check?

Well, having an ATI card gives you two options for video card drivers:  fglrx and aiglx.

Did you install either?

What does:

```
fglrxinfo
```

produce?

You may want to look at the first post in this thread which has some links to tutorials for ATI cards.

[http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)

---

### Post by kh1116 on 2007-08-21
ran "fglrxinfo"

display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R200 20060602 AGP 1x x86/MMX+/3DNow!+/SSE TCL
OpenGL version string: 1.3 Mesa 6.5.2


********************
i checked the xorg file and i am using the ati driver. i looked at my current xorg file and it showed this

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"Generic Video Card"
	Monitor		"Generic Monitor"
	DefaultDepth	24
```

 i looked at one of the back up xorg files and it showed this ```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon RV250 If [Radeon 9000]"
	Monitor		"Envision D55"
	DefaultDepth	24
```

i had to run ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` last boot for unknown reasons, although desktop effects wasnt working prior to that.

---

### Post by Ek0nomik on 2007-08-22
Well you will probably want to look at the link I provided you with.

If any of the guides call for installing FGLRX, you can refer to this:  [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

It's a real easy way to install the propriety ATI drivers.

---

