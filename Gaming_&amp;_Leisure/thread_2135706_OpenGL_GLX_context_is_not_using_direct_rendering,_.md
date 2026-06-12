---
title: "OpenGL GLX context is not using direct rendering, which may cause performance problem"
date: 2013-04-15
forum: Gaming &amp; Leisure
---

### Post by stanrogo on 2013-04-15
Hi guys,

So yep, when starting steam I get this error as in the title. This becomes even more apparent when I try to play e.g. Cubemen 2, who's interface looks very weird, like it's not rendering it properly as shown below:
[ATTACH=CONFIG]241387[/ATTACH]
I'm using an AMD card and Direct Rendering is enabled apparantly according glxinfo:

```

stanrogo@stanrogo-desktop:~$ glxinfo | grep rendering
direct rendering: Yes

```

fglrxinfo returns:
```

stanrogo@stanrogo-desktop:~$ fglrxinfo
display: :0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6850 X2
OpenGL version string: 4.2.12002 Compatibility Profile Context 9.012

```

So what could be the problem? I am using AMD proprietary drivers in order to have catalyst control centre to make sure I can have a triple screen set up.

Any help would be much appreciated!

---

### Post by myromance123 on 2013-04-15
> AMD Radeon HD 6850 X2 What does the X2 mean? Are you in CrossFire?

What version of Ubuntu are you using? Also, is it 32Bit or 64Bit? The AMD driver you have installed, did you install it via Ubuntu's Additional Drivers application? Or did you download and manually install the drivers from AMD's website?

It would also greatly benefit you and us, if you could run Steam from a Terminal.
```
steam
```
Now, when you try to run Cubemen 2 are there any errors that pop up in the Terminal window?

---

