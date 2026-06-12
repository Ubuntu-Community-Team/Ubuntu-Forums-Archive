---
title: "Lucid display problems on Inspiron 8500"
date: 2010-07-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Citizen_Kane01 on 2010-07-28
I am installing 10.04 on a Dell Inspiron 8500 and having the following problem:

Installs fine, but graphics are kind of ghosted (strange horizontal artifacts and a double mouse pointer)

Enabling recommended hardware driver (NVIDIA accelerated graphics driver (version 96)) makes matters worse. After restart the display is completely unusable - only loads of white horizontal artifacts across the whole screen.

Restarting in failsafe graphics mode brings up a perfect display.

I have tried installing all the NVIDIA drivers, but none of them work.

Any help please? I can't find anything helpful about this on the internet.

---

### Post by Citizen_Kane01 on 2010-08-01
The exact details on the graphics card is:
Nvidia Corporation NV28 [GeForce 4 Ti 4200 Go AGP 8x] (rev a1)
Subsystem: Dell Device 0179

---

### Post by Citizen_Kane01 on 2010-08-01
OK - So I have got this working well enough. Here is my rough guide:

Start the system in safe graphics mode by holding down the 'shift' key while booting. This will get you into the grub boot menu. 

Select 'Recovery mode' of your latest kernel and then select 'failsafe graphics'. You should now be able to get into a workable Ubuntu graphical interface.

The trick is that the newer Ubuntus are upgrading the X server system (which controls the graphics amongst others) to 'Nouveau'. This does not work with some older cards. Go into System, Administration, Synaptic package manager and enter 'nvidia' into the search box. Mark for uninstall the 'xserver-xorg-video-nouveau' and for install 'xserver-xorg-video-nv'. I have done loads of trial and error here, so included is a screenshot of all the Nvidia stuff I have installed. (copy this on your system)

On top of this, the proprietary Nvidia drivers dont work either on newer kernels - so you have to remove the old configuration file that may have been created as you were trying to get things working. Open a terminal (Applications, Accessories, Terminal) and type or paste:
```
sudo rm /etc/X11/xconfig/xorg.conf
``` 

Restart your computer. You should now have graphics as expected. Trouble is still that you will have no accelerated graphics, so Desktop Visual Effects and Compiz WILL NOT WORK!

A workaround to get compositing (needed for docks and widgets) working is to enable Metacity compositing. Hit <Alt>F2 and enter:
```
gconf-editor
```

In the interface browse to: apps, metacity, general and tick to enable 'compositing_manager'. You can aslo enable <Alt>Tab switching under 'global_keybindings', 'switch_windows'

This should give you a functional desktop environment on your Inspiron 8500.

If anybody knows how to enable visual effects, please, please post here.

---

### Post by markp1989 on 2011-03-31
> **Citizen_Kane01 said:**
> OK - So I have got this working well enough. Here is my rough guide:

Start the system in safe graphics mode by holding down the 'shift' key while booting. This will get you into the grub boot menu. 

Select 'Recovery mode' of your latest kernel and then select 'failsafe graphics'. You should now be able to get into a workable Ubuntu graphical interface.

The trick is that the newer Ubuntus are upgrading the X server system (which controls the graphics amongst others) to 'Nouveau'. This does not work with some older cards. Go into System, Administration, Synaptic package manager and enter 'nvidia' into the search box. Mark for uninstall the 'xserver-xorg-video-nouveau' and for install 'xserver-xorg-video-nv'. I have done loads of trial and error here, so included is a screenshot of all the Nvidia stuff I have installed. (copy this on your system)

On top of this, the proprietary Nvidia drivers dont work either on newer kernels - so you have to remove the old configuration file that may have been created as you were trying to get things working. Open a terminal (Applications, Accessories, Terminal) and type or paste:
```
sudo rm /etc/X11/xconfig/xorg.conf
``` 

Restart your computer. You should now have graphics as expected. Trouble is still that you will have no accelerated graphics, so Desktop Visual Effects and Compiz WILL NOT WORK!

A workaround to get compositing (needed for docks and widgets) working is to enable Metacity compositing. Hit <Alt>F2 and enter:
```
gconf-editor
```

In the interface browse to: apps, metacity, general and tick to enable 'compositing_manager'. You can aslo enable <Alt>Tab switching under 'global_keybindings', 'switch_windows'

This should give you a functional desktop environment on your Inspiron 8500.

If anybody knows how to enable visual effects, please, please post here.

Thanks you.

picked up one of these laptops in a charity shop for £27.

followed your post and got it working perfectly :)

---

