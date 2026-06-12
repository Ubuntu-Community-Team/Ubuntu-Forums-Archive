---
title: "Composite Extension and Beryl Help"
date: 2007-05-17
forum: Desktop Effects &amp; Customization
---

### Post by Nubifier on 2007-05-17
I am using an Nvidia 6600 video card with the latest drivers installed.

When I try to turn on Desktop Effects I get the message
"The Composite extension is not available"

When I try to launch Beryl it gives me this message

```
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
Window manager warning: "" found in configuration database is not a valid value for keybinding "toggle_shaded"

```

My /etc/X11/xorg.conf looks like this

```
Section "Extensions"
	Option		"Composite"	"1"
EndSection

```

I have followed a number of people's instructions and none have helped me, so if anyone has any clue what's going on here, I would appreciate any help.

EDIT: I am using Ubuntu 7.04

---

### Post by Timtro on 2007-05-18
*bump*

I don't think I can be of much help. I have no experience with Nvidia. Hopefully though, this post will bump your message so someone will see it.

---

### Post by Nubifier on 2007-05-21
Well, considering no one helped, and I want to make sure anyone who has this problem to have help...

Just run Envy... works so well.

---

