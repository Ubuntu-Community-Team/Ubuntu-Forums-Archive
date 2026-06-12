---
title: "XComposite extension failed in Beryl"
date: 2007-05-20
forum: Desktop Effects &amp; Customization
---

### Post by Mykle87 on 2007-05-20
I just don't understand why I can't get Beryl to work. I have followed the installation and uninstall guides on the Beryl Wiki and the Feisty Wiki without luck. I noticed this in terminal during the installation on the Feisty Wiki

```
Checking for XComposite extension               : failed
```

What am I doing wrong? I am running 7.04 i386 with a ati x850xt. I am running the ati driver in the restricted drivers. I have beryl running but it isn't working. I'd appreciate the help.

---

### Post by Ub1476 on 2007-05-20
The composite error means that you are not running in XGL, but a regular Gnome session.

First remove beryl:

```
sudo aptitude remove xserver-xgl beryl beryl-core beryl-manager beryl-plugins beryl-plugin-data beryl-settings beryl-setting-bindings libberyldecoration0 libberylsettings0 libemeraldengine0
```

Now follow this guide: [Linky]("http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28ATI.29")

Scroll down to..:
Alternate method: Using closed source FGLRX drivers from ATI.
..and follow the guide from there.

---

### Post by Mykle87 on 2007-05-20
Now after I boot into Gnome with XGL and launch beryl-manager, my screen goes black.

---

### Post by Ub1476 on 2007-05-20
So, it's working for you to log into XGL, but beryl crashes? Type:

```
beryl
```

.. in the terminal and copy/paste what you get in here. Also what beryl v. are you using?

```
beryl --version
```

---

### Post by Mykle87 on 2007-05-20
```

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

```

```

beryl-core 0.2.0

```

---

### Post by motorhead on 2007-05-20
I have the exact same problem. The screen goes black but if you try to rotate the cube (ctrl+alt+Key_Up) you can see the big beryl diamond. The cube works but just that.

Anyone else with this problem that has been able to fix it?

Thanks in advancce.

---

### Post by motorhead on 2007-05-20
ok, i  fixed it:

I first removed beryl with:
```

sudo aptitude purge beryl emerald-themes

```

Then i made sure i had universe disabled. System -> Administration -> Software Sources

Then
```

sudo aptitude update

```

Finally
```

sudo aptitude install beryl emerald-themes

```

That worked for me. Hope this helps someone.

Here the proof!
[http://img171.imageshack.us/img171/6150/screenshot2dl2.png](http://img171.imageshack.us/img171/6150/screenshot2dl2.png)

---

### Post by Mykle87 on 2007-05-21
Well, it didn't help me out. After I reinstalled beryl, I am still getting the same output from beryl

```

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

```

Should I just give up? Is anyone successfuly running beryl with an ati x850xt?

---

### Post by Mykle87 on 2007-05-21
Also I am missing shutdown and restart when running XGL

---

### Post by Mykle87 on 2007-05-23
[http://www.mepis.org/docs/en/index.php/ATI_supported_cards](http://www.mepis.org/docs/en/index.php/ATI_supported_cards)

Ok so my card is supported according to that wiki. Why isn't it working then?

---

### Post by ViciousDotOrg on 2007-05-27
Same issue, same video card.  Go figure.

---

### Post by ViciousDotOrg on 2007-05-27
I used the alternate installation listed on ubuntu guide:

[http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28ATI.29](http://ubuntuguide.org/wiki/Ubuntu_Feisty#How_to_install_Beryl_.28ATI.29)

And all is well.

---

### Post by motorhead on 2007-05-28
Check if you're beryl is configured like this:

Right click on diamond icon-> Advance Beryl Options -> Rendering Platform -> Force XGL
                           *                          *                               ->  Binding -> XGL Binding
                           *                          *                               ->  Rendering -> XGL Rendering

---

