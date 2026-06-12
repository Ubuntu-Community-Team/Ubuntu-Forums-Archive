---
title: "Beryl and Radeon Xpress 1100 (Feisty)"
date: 2007-04-24
forum: Desktop Effects &amp; Customization
---

### Post by nesquik on 2007-04-24
I tried several guides, re-installed ubuntu a hundred times, it still doesn't work.

Could somebody pleeease explain the steps/copy links to instructions I should follow?

Thank you!

(I'm an absolute beginner.)

---

### Post by Seisen on 2007-04-24
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu")

---

### Post by nesquik on 2007-04-24
And what next? XGL, AIGLX or ATI?

---

### Post by nesquik on 2007-04-27
I followed the instructions for XGL.

When I log into an XGL session and start beryl, this error appears:

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



        I think my graphics card bus is on :1.5... How can I change the beryl settings for that?

---

### Post by woland on 2007-04-28
Try using this guide:
[http://ubuntuforums.org/showthread.php?t=399643](http://ubuntuforums.org/showthread.php?t=399643)

Reading all these calls for help with ATI cards, it seems that they are yet to fix the compatibility issues with XGL and ATI with a version of Beryl in multiuniverse repositories. Try using the one from ubuntu.beryl-project.org.

---

### Post by nesquik on 2007-05-02
Thanks! woland's link worked for me.

---

### Post by joe.turion64x2 on 2007-05-06
Has anybody actually made Beryl + XGL work in Ubuntu 7.04 with a Radeon Xpress 1100?

---

### Post by nesquik on 2007-05-11
Yes, me. Follow woland's link.

---

### Post by patrickfromspain on 2007-05-11
I have made it work on my girlfriend's laptop. Took me less than 20minutes. 

How to install the ati drivers, I used method one:
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

How to install beryl:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)

---

### Post by joe.turion64x2 on 2007-05-13
> **patrickfromspain said:**
> I have made it work on my girlfriend's laptop. Took me less than 20minutes. 

How to install the ati drivers, I used method one:
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

How to install beryl:
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_XGL)
Did you install extra ATI drivers? Isn't that enough with those provided by the "Restricted Drivers Manager"?

---

### Post by joe.turion64x2 on 2007-05-13
Beryl is now working in my laptop with ATI Radeon Xpress 1100. I just followed this guide [http://ubuntuforums.org/showthread.php?t=399643](http://ubuntuforums.org/showthread.php?t=399643) posted above by woland. The further step I took to preserve my Beryl installation (because then Ubuntu attempted to update the packages thus breaking Beryl) was to **Lock the version** of all the Beryl related packages in Synaptic.

---

