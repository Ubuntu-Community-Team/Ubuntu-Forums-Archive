---
title: "Beryl loads but won't start up"
date: 2007-02-08
forum: Desktop Environments
---

### Post by pahn on 2007-02-08
Hi all,

I just installed Ubuntu 6.10 dual boot on my laptop tonight.  I've been trying to get beryl to work as well.  I used the guide from [http://ubuntuguide.org/wiki/Ubuntu_Edgy]("http://ubuntuguide.org/wiki/Ubuntu_Edgy") and got it installed correctly... eventually.  I actually got beryl working for about 10 minutes as well.  However, after I restarted my computer, beryl will load into the task manager but will not start up when I click beryl-manager > Select Window Manager > Beryl.  It always reverts to my default ubuntu window manager.  My laptop has an Nvidia graphics card and I believe I installed the drivers correctly.  I followed the instructions from the above link.  I don't know where to start in fixing this.

---

### Post by jpneron on 2007-02-08
It sounds similar to a problem I had. This thread might help:

[http://www.ubuntuforums.org/showthread.php?t=356082]("http://www.ubuntuforums.org/showthread.php?t=356082")

---

### Post by pahn on 2007-02-08
Jean,

I tried the commands listed on the link you posted but it did not help.  I'm new to linux and I'm not real sure what the XGL is or how it is linked to beryl.  However, I did try running both on my terminal and got this output

jim@jim-laptop:~$ beryl&
[1] 5517
jim@jim-laptop:~$ **************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

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

Relaunching beryl with __GL_YIELD="NOTHING"
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

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

Reloading options

[1]+  Segmentation fault      (core dumped) beryl

jim@jim-laptop:~$ beryl&
[1] 5517
jim@jim-laptop:~$ **************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

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

Relaunching beryl with __GL_YIELD="NOTHING"
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

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

Reloading options

[1]+  Segmentation fault      (core dumped) beryl


So beryl does not work either way.  It keeps reverting to my default ubuntu window manager.  I want  to try reinstalling beryl and maybe my drivers because I had some trouble with the wget commands in my sources.list file and could not add the keys for authentication.  I think I got it to work eventually, but I might just try a fresh start.  If anyone can give me some suggestions or link me to a good reinstall tutorial for linux apps I'd appreciate it.

---

### Post by shareMenaPeace on 2007-02-08
Hi check your sources under
System -> Administration -> Software sources -> 3rd Party


Or in
> /etc/apt/sources.list




Check this guide about your repositorys
[http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/)

To reinstall beryl try this - but make sure you have repos with auth key working.
[http://ubuntuforums.org/showthread.php?t=354228&highlight=reinstall+beryl](http://ubuntuforums.org/showthread.php?t=354228&highlight=reinstall+beryl)

---

### Post by pahn on 2007-02-09
Thanks for your advice everyone.  Turns out I didn't have to reinstall beryl, and the problem wasn't with my graphics driver.  I followed some your links and tweaked beryl till it worked.  Now I just have to try to get my wireless working...

---

