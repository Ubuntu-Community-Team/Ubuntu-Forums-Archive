---
title: "HELP: Beryl on Feisty"
date: 2007-08-06
forum: Desktop Effects &amp; Customization
---

### Post by alvino on 2007-08-06
hi gurus
i've managed to install beryl on my feisty
the problem is now whenever i "Select window Manager" then beryl it doesnt work
it keeps going back to Metacity (GNOME Manager)

BTW, i followed the guide from [http://ubuntu1501.blogspot.com/2007/04/beryl-in-feisty-with-xgl.html](http://ubuntu1501.blogspot.com/2007/04/beryl-in-feisty-with-xgl.html)

whats wrong?

---

### Post by nichipet on 2007-08-06
This is a common problem. I am stuck at the same point. I'll be watching this thread to try anything people suggest. I'll let you know if I make some progress.

Given the guide you used, I'm guessing you are using a Dell Inspiron 1501. If so, I'm not convinced Beryl will work. A friend of mine has the same laptop with Ubuntu 7.04 so if a fix is found for it on there, I'll try to set her laptop up as well.

By the way, can you give the output for trying in terminal:

```
beryl
```

I think it will say something like this:

> beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

At least that's what I get.

---

### Post by alvino on 2007-08-06
hi
i'm not using a Dell 1501
I have my own desktop P4 2.8 running on an Asus P4P800-X Motherboard.
512MB RAM and a 9600 ATI Radeon.

Running beryl at the terminal gave this output:

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension

How come its showing AIGLX?
The guide I followed was suppose to make it GLX right? :confused:
Any gurus that can help?
Or maybe instead of beryl what other easier apps we can use to do the same effect?

---

### Post by Waappu on 2007-08-07
Hi

You need login to XGL session.

---

### Post by alvino on 2007-08-07
Waappu: Tried that doesnt work too :( I dont get any effects at all and on top of that everything is slowwww and my title bar goes missing. Even when I select compiz or beryl or metacity for that matter...

Any more ideas??

---

### Post by alvino on 2007-08-07
YES!!! Finally got it working thanks to this guide:
[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Beryl_.28ATI.29)

Manage to get it to work... :guitar:

Rock n roll baby...

Thanks guys!

---

### Post by alvino on 2007-08-07
However when I run beryl in terminal I get this:

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

Is there any problems with this?

---

