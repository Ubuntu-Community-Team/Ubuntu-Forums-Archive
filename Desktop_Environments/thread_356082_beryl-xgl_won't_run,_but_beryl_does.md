---
title: "beryl-xgl won't run, but beryl does?"
date: 2007-02-08
forum: Desktop Environments
---

### Post by jpneron on 2007-02-08
I had version 0.1.1.1 of beryl working, with the emerald theme & all was good.

Then I noticed that I could add the beryl repositories & get the latest version, so I did, and now I've got trouble. 

Basically, it comes down to the fact that beryl-xgl just crashes. Here's what I get when I run beryl-xgl in a terminal window:

jean@jean-desktop:~$ beryl-xgl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Segmentation fault (core dumped)

However, if I just run beryl, it works fine:

jean@jean-desktop:~$ beryl&
[1] 2228
jean@jean-desktop:~$ ***********************************************************
***
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

beryl: No XKB extension
beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: No GLXFBConfig for default depth, falling back on visinfo.
Reloading options

At this point, all is well. Beryl seems to be working, all the features do what they are supposed to, etc. 

I've searched the forums, and found all kinds of different things, but nothing seems to fix the problem. I've removed & reinstalled beryl & the emerlald themes, but that didn't help. 

I'm running Edgy, with the Nvidia drivers.

I've run out of ideas & things to try. Does anyone have any suggestions?

Thanks.

Jean

---

### Post by jpneron on 2007-02-08
Well, as a complete, brute force, totally kludgy work around, I linked beryl-xgl to beryl:

```
sudo mv /usr/bin/beryl-xgl /usr/bin/beryl-xgl.orig 
sudo ln -s /usr/bin/beryl /usr/bin/beryl-xgl
```

And now it all works.

Warning: I'm not sure will happen when the next release comes out. The link may or may not be preserved, which may or may not be a good thing. Probably the safest thing would be to

```
sudo rm -f /usr/bin/beryl-xgl
```

before the upgrade.

Hope this helps someone.

Jean

---

### Post by PriceChild on 2007-02-08
Thanks for this find... I'm currently finding out more :)

---

