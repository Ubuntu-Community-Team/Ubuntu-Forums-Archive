---
title: "nvidia driver help!!"
date: 2007-08-28
forum: Desktop Environments
---

### Post by nickkov89 on 2007-08-28
ok well i was trying to install compiz and to tell the truth i had no idea what i was doing and i ended up uninstalling the nvidia drivers so when i start up ubuntu i get some crazy error message filled with weird symbols saying something like:

Failed to start the x server(your graphical interface)

and something like

failed to load module "nvidia" (module does not exist)
there was a lot more to it but these are the main errors

now my terminal loads, but thats it, i guess i have to install my nvidia drivers onto it again but i dont know how using the terminal, maybe thats not the problem, i dont know, please help thanks a lot

---

### Post by DarkN00b on 2007-08-28
In the command prompt screen you see, type the following:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo nano /etc/X11/xorg.conf
```

The X in X11 is upper case - this is important.

Put in your password and use the arrow keys to go down to the "Device" section. For Driver put "vesa".

Now press ctrl+o and hit enter then hit ctrl+x to exit. Now type:

```
sudo reboot now
```

to reboot your computer. The machine will now reboot and you'll be able to log into a graphical desktop. This is the most basic video driver in Linux, so there will be no acceleration.

Now go to System > Administration > Restricted Drivers Manager. You should be able to install the proprietary Nvidia driver from there. Check the /etc/X11/xorg.conf to make sure the Device section says "nvidia" before you reboot. From here you should be able to reboot and load your Nvidia drivers.

---

### Post by Nythain on 2007-08-28
or you could just try
sudo apt-get install nvidia-glx (or nvidia-glx-legacy or nvidia-glx-new depending on your card)

that is if all you did was just uninstall teh drivers... taht should get them going again, you might have to re-edit your xorg.conf and change the driver from "vesa" or "nv" back to "nvidia" if it isnt already...

---

