---
title: "Beryl on ATI Radeon X1300"
date: 2007-07-03
forum: Desktop Effects &amp; Customization
---

### Post by shiznatix on 2007-07-03
I have an ATI Radeon X1300 card and I have heard that it is unsupported from some websites and that it is supported if I use XGL somehow.

Basically, right now I am using the restricted ATI drivers so Beryl won't work obviously. Is there a decent tutorial somewhere that will show me how to turn to the XGL drivers and install Beryl or is this a situation that is pretty much useless?

---

### Post by Waappu on 2007-07-03
Hi

Here is one guide
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)
start reading from "Alternate method: Using closed source FGLRX drivers from ATI."

---

### Post by advanracing62 on 2007-07-05
I have Beryl running on my 1300 in XGL, however the title bars don't work, nor the cube or rain/snow. Otherwise, it works. I'm using the restriced driver though.

---

### Post by stillwaters130 on 2007-07-05
I've found these two sites to work perfectly for me:
[http://www.howforge.com/how-to-setup-fglrx-for-ubuntu-feisty](http://www.howforge.com/how-to-setup-fglrx-for-ubuntu-feisty)
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL#Adding_an_Xgl_login_session](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL#Adding_an_Xgl_login_session)

The first one gives you a link to a patch which was what I needed to fix my problems with the fglrx driver.
Second one shows you how to make an xgl session.

I have a Radeon X1400, so our cards are pretty close; hopefully this will work for you.

---

### Post by advanracing62 on 2007-07-06
^ tried that yesterday, not long after you posted it- no luck for me... maybe for others. Thanks for the links though!

---

### Post by stillwaters130 on 2007-07-06
Try running beryl-manager from the terminal.  Does it give you any errors, that beryl-xgl is of a different version from the plugins?  That happened to me too; you have to go into synaptic and make sure everything that has to do with beryl is version 0.2.0~0beryl1.

If those aren't the errors, but you still are getting errors, post them here.  You can try running just beryl from the terminal, too, and see what happens there.

---

### Post by advanracing62 on 2007-07-06
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0

that's what I'm getting when I run beryl in terminal- Some reason none of the fixes seem to work in this machine... no clue why

---

### Post by stillwaters130 on 2007-07-06
Ok - I get those same errors when I run beryl from the terminal, and my beryl works flawlessly, so I don't think that's the problem.  What's the output when you run beryl-manager from the terminal?

---

### Post by advanracing62 on 2007-07-06
if i run that command it just opens the manager. As it is now, i can run under Compiz with helidor. Which gives me most effects, just no cube and fun little rain/snow things.

---

### Post by pardesi on 2007-07-06
then enter windows manager and choose beryl

---

### Post by advanracing62 on 2007-07-06
that is working at this point- if i select emerald I lose my close/minimize, I do have emeral themes installed-  though i suppose emerald is just a theme manager. Still no cube/visual effects

---

### Post by pardesi on 2007-07-06
for no top bars
```
sudo gedit /etc/X11/xorg.conf
```
add this line
```
Option      "AddARGBGLXVisuals" "True"
```
below the line in the device sction that tells u about ur drivers

also see [here](http://ubuntuforums.org/showthread.php?t=476716)
for every other doubt(be patient while reading)

enjoy

---

### Post by advanracing62 on 2007-07-06
Section "Device"
	Identifier	"Generic Video Card"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"

in that section? Sorry, I don't want to jack things up by putting it in the wrong spot. Based on some of the other xconf I've seen... looks like I really don't have a video driver installed at all, with this defaulting to generic

---

### Post by stillwaters130 on 2007-07-06
The "Generic Video Card" is just the default name for the video card.  You can change it to your actual card name if you want.  It sounds like your driver is not correctly installed... type 'fglrxinfo' into the terminal.  If it outputs something about ATI, then you're good, if it's Mesa, it's not installed correctly.

---

### Post by advanracing62 on 2007-07-06
ATI comes up- so I'm good on that.

---

### Post by stillwaters130 on 2007-07-06
Are you booting into an xgl session, or just your regular gnome session?  When you come to the login screen, there should be an options button or something like that.  If you followed the instructions to create an xgl session that I gave you above, then there should be another session you can choose called xgl or gnome with xgl (there should be other options too, like failsafe gnome and failsafe terminal).

It sounds like your driver is installed correctly, but (at least on my computer), 3D acceleration will **not** work unless I'm in an xgl session.  Here's the link again in case you need it:

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL#Adding_an_Xgl_login_session](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL#Adding_an_Xgl_login_session)

You don't need to worry about the beryl stuff on that page, just the xgl session.

---

### Post by advanracing62 on 2007-07-06
nod- I'm in XGL, it auto boots into this session now as it's the default. I suppose I'll just have to not worry about the cube and Emerald for now.

---

### Post by stillwaters130 on 2007-07-06
Hmmm, I honestly don't know what else the problem could be :-/  I wish I could help you more, but I really just have no other suggestions.  I hope you can manage to get help from someone else and fix your problem.

---

### Post by advanracing62 on 2007-07-06
Thanks for your help thus far! I am just going to say five it for now... maybe a future release from either ATI or Beryl will correct this issue. 
The good thing is my home PC works like a charm with NVidia!

---

### Post by greymongrey on 2007-07-06
I did get Beryl working with my X1300 but it was always buggy. I decided stable was better than not stable.

---

### Post by stillwaters130 on 2007-07-06
Yeah, I have a nVidia on my desktop computer too, and I got everything working fine with that, it's just been my laptop with an ati card that gave me trouble... I guess ati's don't go too well with linux at this point :-/

---

