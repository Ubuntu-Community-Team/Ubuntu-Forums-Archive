---
title: "Beryl not allowing switch to Beryl Manager"
date: 2007-06-12
forum: Desktop Effects &amp; Customization
---

### Post by coolbot on 2007-06-12
Hello every one am having a small problem with beryl, when i start beryl and select switch to beryl under switch to beryl manager the open windows just refresh and it reverts it self back to standart gnome (metacity).
i have appled all the proper drivers and patches and is still no go, my graphics card is supported its a Radeon 9550 256 AGP. if some one can help me figure this out thank you.

---

### Post by raul_ on 2007-06-12
Try starting Beryl Manager through a terminal (just type beryl-manager) and try switching to Beryl. A lot of text will appear in the terminal, and maybe if you post it here someone will be able to help you

---

### Post by coolbot on 2007-06-12
ok this is what error message i got from Terminal

* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

---

### Post by raul_ on 2007-06-12
> **motorhead said:**
> Check if you're beryl is configured like this:

Right click on diamond icon-> Advance Beryl Options -> Rendering Platform -> Force XGL
                           *                          *                               ->  Binding -> XGL Binding
                           *                          *                               ->  Rendering -> XGL Rendering

try it. At least now you know what to look for :)

---

### Post by coolbot on 2007-06-12
nuthin am getting this at the end of the terminal message

* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension
Window manager warning: Lost connection to the display ':0.0';
most likely the X server was shut down or you killed/destroyed
the window manager.

---

### Post by rolf-c on 2007-06-12
check out a similar issue in this thread - [http://ubuntuforums.org/showthread.php?p=2691287]("http://ubuntuforums.org/showthread.php?p=2691287").   this user was having the same XComposite error message that you are getting.

---

### Post by raul_ on 2007-06-12
[http://forum.beryl-project.org/viewtopic.php?f=36&t=3228]("http://forum.beryl-project.org/viewtopic.php?f=36&t=3228")

Did you create a separate XGL session?

---

### Post by coolbot on 2007-06-12
> **raul_ said:**
> [http://forum.beryl-project.org/viewtopic.php?f=36&t=3228]("http://forum.beryl-project.org/viewtopic.php?f=36&t=3228")

Did you create a separate XGL session?

please explain am new to this. its gana take me awhile to get used to the lingo

---

### Post by raul_ on 2007-06-12
First, did you install the official ATI drivers?

---

### Post by coolbot on 2007-06-12
> **raul_ said:**
> First, did you install the official ATI drivers?

no i did not i guess i would get them off the ati site?

---

### Post by raul_ on 2007-06-12
> **coolbot said:**
> **i have appled all the proper drivers and patches** and is still no go, my graphics card is supported its a Radeon 9550 256 AGP. if some one can help me figure this out thank you.

What have you done then?

---

### Post by coolbot on 2007-06-12
i actually ment the resricted drivers. i downloaded the ati driver there in .run formatt how to i run this.

---

### Post by raul_ on 2007-06-12
Take a look at this link [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")

---

### Post by coolbot on 2007-06-13
ok this is what am getting now in terminal

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
Checking for non power of two texture support   : failed

Support for non power of two textures missing
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

---

