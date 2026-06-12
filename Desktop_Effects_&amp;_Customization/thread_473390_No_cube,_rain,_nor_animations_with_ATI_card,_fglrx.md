---
title: "No cube, rain, nor animations with ATI card, fglrx, xgl, &amp; beryl in 7.04 on amd 64"
date: 2007-06-14
forum: Desktop Effects &amp; Customization
---

### Post by ferunandesu on 2007-06-14
I followed this howto

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

and got everything setup properly, but I still have NO CUBE, NO RAIN, and NO ANIMATIONS.

I've looked through as many threads here as I could, but none of them solved my problem. Desktop effects are enabled and wobbly windows works fine. I have the red ruby and I've been toying with the Beryl Settings Manager for hours. At the moment, ctrl alt + direction will only allow me to switch between workspaces. 

Horizontal Virtual Size: 4
Vertical Virtual Size: 4
Desktops: 4
Workspaces: 4

"fglrxinfo" outputs:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X700 PRO
OpenGL version string: 2.0.6334 (8.34.8)

"beryl" outputs:


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

I don't know what the problem is... Perhaps it's just not going to happen, perhaps I just can't make heads or tails of the Beryl Settings Manager, or perhaps it has something to do with **GLX_SGIX_fbconfig is missing**

---

### Post by ferunandesu on 2007-06-14
My only idea at the moment is to attempt to use AIGLX with an open source ATI driver, rather than using XGL with fglrx.

Does anyone have any thoughts whatsoever?

EDIT: Or perhaps just use Compiz.

---

### Post by ferunandesu on 2007-06-14
Still no posts? If none by tomorrow, then I'll attempt running beryl through the open source drivers and AIGLX. Although, I'm guessing that it'll still be sketchy since I heard, in the wind, that the open source drivers don't work well on x700's.

---

### Post by zero244 on 2007-06-14
Watch out Beryl in my opinion works best with XGL......if you look in the settings make sure you have desktop switcher enabled and makes sure you have at least two workspaces setup.
Then hold down alt cltr and drag your mouse.
Randomly changing settings in beryl can get you in trouble.
Since beryl seems to be working make sure its not just a setting problem.
Once you get beryl working the way you like leave it alone......and watch what you update or you might kill it.
going from xgl to aiglx is not the easiest thing to do......and you might screw things up in the process.
With my Video card XGL is the best way to go.
Good luck.

---

### Post by ferunandesu on 2007-06-14
No go, with beryl, ctrl + alt and dragging the mouse will only bring up the rectangular selection thingy. With compiz, however, the cube works fine.

---

### Post by whiteolorin on 2007-06-15
I followed the steps found on the link below for installing beryl with my x800.
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)

It shows how to do it with both the open source ati drivers and the fglrx drivers. Both ways seemed to work, but using the fglrx drivers made everything run a lot smoother. I hope that helps. ;)

---

### Post by zero244 on 2007-06-15
Also to activate rain......click on the water feature in the window manager settings.........then to activate it press shift-F9 to turn on and off the rain effect.

---

### Post by timcredible on 2007-06-15
i have it all working with a dual-core intel 64 bit and ati x1500 card.  i even installed the extra plugins via synaptic, and it's snowing on my desktop.  anyway, i forget what how-to i used, but i installed the proprietary ati drivers, if that helps.

---

