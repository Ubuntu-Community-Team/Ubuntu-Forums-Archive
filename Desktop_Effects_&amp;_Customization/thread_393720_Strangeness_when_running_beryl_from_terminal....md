---
title: "Strangeness when running beryl from terminal..."
date: 2007-03-26
forum: Desktop Effects &amp; Customization
---

### Post by herbster on 2007-03-26
I am using Beryl 0.3.0svn, all is bootyful, works great etc. and Beryl been working great for me for a couple months now since installed, but out of curiosity today I tried running Beryl from the command line instead, and I got the following:

```
bobby@bobby-ubuntu:~$ beryl
**************************************************************
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
```

So I startup into my XGL session, and usually Beryl automatically loads (or I just do the right-click on the diamond and select it as window mgr like everyone else), but I had it running,  clicked on Metacity and then did the above and what's more is my workspaces/windows were titlebar-less and pretty much frozen, could mouse around and all but nothing more with regards to windows. Had to load up Beryl from the right-click on diamond to get order restored.

Any ideas what those errors mean (they are foreign lingo to me)?

---

### Post by adam.tropics on 2007-03-26
since you're using xgl, you would put in terminal,
```
beryl-xgl
```then it will work.<----he says....confidently!!

---

### Post by davtaine on 2007-04-03
...and he knows what he speaks :)  after that everything works nicely again. thanks

---

### Post by herbster on 2007-04-03
Yup, it sure did, thanks!!

---

