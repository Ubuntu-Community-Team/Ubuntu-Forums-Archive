---
title: "Radeon x1650 and desktop effects are now working"
date: 2007-11-13
forum: Desktop Effects &amp; Customization
---

### Post by sschlangen on 2007-11-13
Ok there has been a lot of threads on this and advice about how to get the desktop effects going with the radeon x1650 and i would like to think i exhausted all resources and would like to put a one place find on how to get the card working with the desktop effects or rather how it worked for me. I never once had a issue getting the restricted drivers to work my problem was that once the driver was running and enabled i kept getting a composite extension not found....So enough explaining i will just show you what i did step by step

[COLOR="Red"]1st things 1st.....This is the most crucial part!!!!!!!![/COLOR]


[COLOR="Black"] Enable "restricted" Repository

Make sure the restricted repository is enabled in /etc/apt/sources.list or this guide will not work!

System > Administration > Software Sources. Check "Proprietary Drivers for Devices (Restricted)" box. 

Disable Composite Extension

In Ubuntu Feisty the Composite extension is enabled by default, however, fglrx does not yet support Composite with DRI. In order to disable Composite you have to edit the xorg.conf file:[/COLOR]

```
gksu gedit /etc/X11/xorg.conf
```

[COLOR="Black"]and add these lines at the end of the file:[/COLOR]

```
Section "Extensions"
        Option  "Composite" "Disable"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection
```

[COLOR="Black"]Install the Driver the Ubuntu Way[/COLOR]

```
sudo apt-get update
sudo apt-get install linux-restricted-modules-generic restricted-manager
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
```

[COLOR="Red"]Note: The second line of the above may not be necessary. If apt says it cannot find the "linux-restricted-modules" package, try line 3. If that fails, check your sources.list (see top of page)

If the system complains about dependencies, use your preferred package manager to download python2.4 and, if necessary, its dependencies. [/COLOR]

[COLOR="Black"]All of this can be found here!!!!!![/COLOR]
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_1:_Install_the_Driver_the_Ubuntu_Way](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_1:_Install_the_Driver_the_Ubuntu_Way)

Now once you verify the driver is working by clicking system>Admin>screen and graphics and cliock on the graphics card tab and sere fglrx is on the setting you are on to step two.

I would like to note that i never once had an issue with getting fglrx working my issue came when i tried to enable the desktop effects and kept getting no composite extension found

[COLOR="Red"]A just a quick little edit and you are on your way!!!!![/COLOR]

Now i didn't find this in the forums and if it was mentioned i apologize now i am just trying to help beginners like me out with stating how I fixed my issue

1.First things first. With a recent ATI card you must use Xgl. It will not work with AIGLX.  The Free radeon driver doesn't support these newer cards. This leaves you with resorting to the proprietary ATI driver (fglrx). This driver doesn't support the Xorg composite extension which is required for AIGLX to work. It's ok, Xgl isn't that much harder to setup.
```
apt-get install xserver-xorg-video-ati
```
2.Activate the driver
```
sudo gedit /etc/X11/xorg.conf 
```
```
 Section "Device"
        Identifier  "ATI Technologies, Inc. ATI Default Card"
        Driver      "fglrx"
        Option      "DesktopSetup" "horizontal"
        BusID       "PCI:1:0:0"
    EndSection
    Section "Extensions"
        Option  "Composite" "0"
    EndSection
```

Verify direct rendering works
```
glxinfo | grep direct
```
Should be yes

Install Xgl
```
apt-get install xserver-xgl
```

Now after that if you dont see a icon or display show that xgl is active go ahead and restart and you should see the XGL activated. I cant remember if i restarted or not. Once that is done go ahead and enable your desktop effects and you shouldnt have  any issues. Only issue i have had so far is in emerald theme it doesnt change on the fly i have to restart. but hey at lease i have desktop effects working.

I would like to give credit on where i found the second part 
[http://www.kittypee.com/2007/05/07/desktop-effects-on-ubuntu-feisty-ati-beryl/](http://www.kittypee.com/2007/05/07/desktop-effects-on-ubuntu-feisty-ati-beryl/)

Hope this gets you rolling.

---

