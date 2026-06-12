---
title: "Beryl Manager crashes and takes me back to log in."
date: 2007-04-14
forum: Desktop Effects &amp; Customization
---

### Post by borimrr on 2007-04-14
I just installed Beryl on Ubuntu Edgy 6.10 and whenever i start it the desktop sort of crashes, show a black screen (where I can type :S), and then takes me to the log in screen. Any idea what the problem is?

Integrated ATI Express 200 64mb

---

### Post by serialdae on 2007-04-14
What drivers are you using with your ATI card?

Can you run glxgears?

Run Beryl --test-only from a console and see what it says

try starting beryl from a console so you can see any error messages that may come up.

---

### Post by borimrr on 2007-04-14
beryl --test-only gives me:
```

Detected xserver: AIGLX

Checking Display: 0.0 ...

Checking for XComposite extension: passed
Checking for XDamge extension: passed
Checking for RandR extension: passed
Checking for Xsync extension: passed

Checking screen: 0 ...

Checking for GLX_SGIX_fbconfig: passed
Checking for GLX_EXT_texture_from_pixmap: passed
Xlib: extension "XFree86-DRI" missing on display ":0.0".
Checking for non power of two texture support: failed

Support for non power of two textures missing

```

From what I remember beryl-manager wouldnt give me any errors. Glxgears run kind of slow and intermitently and when i stop it it says:
Xlib: extension "XFree86-DRI" missing on display ":0.0".

---

### Post by serialdae on 2007-04-14
I am not real up on ati stuff. I see that you are running the ati proprietary drivers - They did not support the older card I set up and the reading I did sounded like they were a bit more dificult to set up than the open source ati driver. I beleive the Beryl wiki goes into setting them up but most of the reading I did said that about the only reason to use them was for tv functions.

---

### Post by borimrr on 2007-04-14
I do the test again and the only thing that appears is that XComposite is failing. In fact i managed to run beryl amanager but i cnat get to get anything form it working, like the cube and window effects.

---

