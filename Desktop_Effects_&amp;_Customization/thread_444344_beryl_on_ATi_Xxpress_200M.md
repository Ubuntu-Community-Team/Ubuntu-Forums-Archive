---
title: "beryl on ATi Xxpress 200M"
date: 2007-05-15
forum: Desktop Effects &amp; Customization
---

### Post by zedhaz on 2007-05-15
after successfully activating xgl and installing beryl according to the instructions on the page 
" [http://www.unix-tutorials.com/go.php?id=696](http://www.unix-tutorials.com/go.php?id=696) ", when a start beryl from command line i get the following,  

"**************************************************************
* Beryl system compatibility check                           *
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
**************************************************************
Is there any way i could get full beryl functionality,coz at the moment beryl window manager isn't loading,or if it does all pages have no window borders,and the cube effect isn't too.

If anyone can help please do.
Oh, my card is an ATi RC410 Radeon Xpress 200M,on a toshiba satellite A100 259.
Thanks in advance.

---

### Post by Izaksly on 2007-05-16
DO u get a white screen ?

---

### Post by Izaksly on 2007-05-16
--------------------------------------------------------------------------------

For those with white screen/cube, try this in terminal to start beryl:

LD_PRELOAD=/usr/lib/fglrx/libGL.so.1.2.xlibmesa beryl --replace &

and then

beryl-manager



----------------------------------------------------------------------------------

I did not create this code, this was given by Yakuza [http://ubuntuforums.org/member.php?u=269008](http://ubuntuforums.org/member.php?u=269008)

but the code works for me. after 10 min the up and low bars fade. but u dont loose anything , give it a try.
thats exactly where i am.

Good Luck!

---

### Post by zedhaz on 2007-05-16
i don't get a white screen,its only that it launches the "fallback window manager", (metacity [gnome window manager]),and the cube effect doesn't work.If i force the beryl window manager,all the windows will not have borders and unmovable.

---

