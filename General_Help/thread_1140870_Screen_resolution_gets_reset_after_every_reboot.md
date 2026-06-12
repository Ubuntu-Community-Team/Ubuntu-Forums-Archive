---
title: "Screen resolution gets reset after every reboot"
date: 2009-04-28
forum: General Help
---

### Post by Azrael Strife on 2009-04-28
Hey,
I have my screen resolution set to 1280*800 from the nVidia X Server Settings utility (propietary), but after each reboot it gets reset back to 1024*768 no matter what. The "save to x configuration file" also does not work, it says "Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.", I got the configuration and edited the configuration file myself (just pasted the config utility's output, so no errors there), the resolution is fine there, but to no effect, any ideas? And any idea why the save to x config file does not work?

Thanks

---

### Post by BKonkle on 2009-04-28
The problem is that the Nvidia Settings program is not set up to run with root privelages, so it can't write to the /etc/X11 directory.  Try using Alt+F2 to open the Run Command dialog, and then enter:

```
gksudo nvidia-settings
```

After entering your password, that should open the settings program with root privelages.

---

### Post by Azrael Strife on 2009-04-28
> **BKonkle said:**
> The problem is that the Nvidia Settings program is not set up to run with root privelages, so it can't write to the /etc/X11 directory.  Try using Alt+F2 to open the Run Command dialog, and then enter:

```
gksudo nvidia-settings
```

After entering your password, that should open the settings program with root privelages.

Thank you, that solved that part, but my resolution still gets reset to 1024*768 after each reboot, despite having it set correctly in the config file.

---

### Post by mihai.ile on 2009-04-29
I still think it has to do with xorg.conf
When you open nvidia settings with admin rights configure the screen to your resolution and also check the Advanced button that is somewhere above the save config to xorg file and see if there is something relevant in there.

---

### Post by zeex on 2009-04-29
> **Azrael Strife said:**
> Hey,
I have my screen resolution set to 1280*800 from the nVidia X Server Settings utility (propietary), but after each reboot it gets reset back to 1024*768 no matter what. The "save to x configuration file" also does not work, it says "Unable to create new X config backup file '/etc/X11/xorg.conf.backup'.", I got the configuration and edited the configuration file myself (just pasted the config utility's output, so no errors there), the resolution is fine there, but to no effect, any ideas? And any idea why the save to x config file does not work?

Thanks

Hi, 

try starting nVidia X Server Settings utility as root then u'll be able to save xorg.conf file 

**$ sudo nvidia-settings** 

Opens the same configuration uitility window and now you can save xorg.conf

tip: *make a backup of xorg.conf first (Alway keep backup)*

---

### Post by phpdonk3y on 2011-04-15
Hi all,

Had this problem myself and walked through the posts here but nothing worked until in I noticed a monitor XML configuration file in my home directory. (I'm using ubuntu 10.04)
[U]

EASY INSTRUCTIONS


1. (Point and click way)[/U]

Use your graphical file browser to navigate to your home folder. Hold down ctrl+H to show hidden files. Navigate down to the .config folder, and inside you will find the monitors.xml file. Right click the file and choose gedit or another text editor to open it up (if you just click it will open in you web browser by default and you can't edit it there). Once open change the numerical values between the <width> and <height> nodes, save and exit.

or
[U]
2. (command line way)[/U]

Open a teminal and type[B]

nano /home/_<place your login usernname here>_/.config/monitors.xml

[/B]This should open the file in the nano program within the terminal window. Use the cursor keys to find the <width> and <height> nodes. Change the numerical values inside the nodes to the desired (valid) screen resolution size then when finished press ctrl+X and then y for yes to save the changes.

reboot your system and the monitor should start in the preset resolution.:KS

If there is no monitors.xml file in the /.config folder, and you have tried the other posts in this thread without success and you have an nvidia graphics card then maybe you could try editing the /.nvidia-settings-rc file, which is also a hidden system file in your home directory. Also look at using the command line tools nvidia-xconfig and nvidia-settings. To learn how to use these command line tools type the following into a terminal 
[B]
>info  nvidia-xconfig

or 

>info nvidia-settings

[/B]good luck.

phpdonk3y.

---

### Post by pyutaros on 2011-05-26
#6 solved the issue for me.  Thanks, phpdonk3y.

---

