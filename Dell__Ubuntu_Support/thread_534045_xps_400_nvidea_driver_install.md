---
title: "xps 400 nvidea driver install"
date: 2007-08-24
forum: Dell  Ubuntu Support
---

### Post by sina91 on 2007-08-24
hi my friend installed linux on my xps for me and beryl and everything was going great till i retardedly deleted the driver by accident and then when beryl crashed and i had to reboot the ubuntu didnt have the driver to run the gui and now im stuck in command line and i cant figure out how to reinstall the driver since command line isnt recognizing my flash drive and i cant find any other way since the drivers to big for floppys

---

### Post by w4ett on 2007-08-24
From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select "nv" as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This will get you to a GUI desktop. then go to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:

```
sudo envy -t
```

This will run the installation script from the terminal....follow the instructions to remove the old attempted driver installation and then install the correct Nvidia proprietary driver.

Good Luck

---

### Post by sina91 on 2007-08-25
thanks for the speedy response ill try it right now

---

### Post by sina91 on 2007-08-27
thanks for your help with getting my gui back up but im having some trouble with the envy protion i hit 2 which is unintall nvidea driver then i hit one to install but in terminal its sawys theres an error with the instalation should i just go to the nvidea site and get it thank i realy apreciate your help

---

### Post by w4ett on 2007-08-27
Are you running envy from the terminal or from the GUI?  Some folks have better luck running in the terminal.

Also you can try from the terminal:

```
sudo apt-get remove nvidia-glx --purge
sudo apt-get remove nvidia-glx-new --purge
```

Then try envy again.

---

