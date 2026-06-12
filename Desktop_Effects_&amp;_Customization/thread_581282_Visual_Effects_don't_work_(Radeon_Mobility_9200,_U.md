---
title: "Visual Effects don't work (Radeon Mobility 9200, Ubuntu 7.10 LiveCD)"
date: 2007-10-19
forum: Desktop Effects &amp; Customization
---

### Post by suain on 2007-10-19
Hi,

I just wanted to test the visual effects of the new gutsy on my notebook, because they should work with my Radeon Mobility 9200 (I think).
I use the live-cd, so advanced configuration is limited.

When I try to set the visual effects to "*normal*" or "*extra*" in "*Appearance*", I got the notice "*Desktop effects could not be enabled*".

*lspci *gives this information:
```
lspci
01:00.0 VGA compatible controller: ATI Technologies Inc M9+ 5C61 [Radeon Mobility 9200 (AGP)] (rev 01)
```

*LIBGL_DEBUG=verbose glxinfo* gives this one:
```
LIBGL_DEBUG=verbose glxinfo
libGL error: XF86DRIQueryDirectRenderingCapable returned false
display: :0  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa project: www.mesa3d.org
```

In "*Screens and Graphics / Graphics Card*" the Driver is "*ati - ATI Mach8, Mach32, Mach64 and RageXL cards*".
The normal 2D Desktop is working fine with this setting, although I don't have any of these cards installed. If I click "Test" without changing anything, I get a blurry trembling picture in low resolution, asking me, If I want to keep the setting (no, I don't). When I choose "*Radeon*" as the Driver, I get the same picture.

Another user in a german forum had the same problem. On his system, visual effects worked fine unter feisty and the last gutsy beta, but not in the final.

Any Ideas to fix this? :confused:

Regards,
Suain

---

### Post by jackbravo on 2007-10-19
Same issue here.

Desktop effects used to work on ubuntu 7.04 using gnome-compiz-manager. But now they don't. I have the same radeon card (9200) on a presario x1000 laptop.

---

### Post by The Belgain on 2007-10-20
Yep, same here: ATI Radeon Mobility 9200 card, using the opensource "ati" driver.

Is this card deemed too slow to run Compiz by the checks?  It was running pretty reasonably under Feisty...

---

### Post by ebash on 2007-10-20
I have a Mobility Radeon 9600 M10 and couldn't enable the "Visual effects". I found this thread [http://ubuntuforums.org/showthread.php?p=3578150]("http://ubuntuforums.org/showthread.php?p=3578150") which provides a solution that works. Just install the XGL server:

```
sudo apt-get install xserver-xgl
```

Then logout and login. In my case after I logged out I restart the X server (hit Ctrl+Alt+Backspace at the login screen). Once you have logged in enable the "Visual effects" once more.

---

### Post by jackbravo on 2007-10-20
in my case installing xserver-xgl didn't work. I'm using the ati driver. I'll try using the radeon driver instead.

---

### Post by ebash on 2007-10-20
Try to use the fglrx driver, it's the one I'm using and XGL works.

---

### Post by avik on 2007-10-20
> **ebash said:**
> Try to use the fglrx driver, it's the one I'm using and XGL works.

Unfortunately, you need to restart after installing the restricted drivers in Gutsy, and that means you can't test this on the LiveCD.  At least that was the case for me.

---

