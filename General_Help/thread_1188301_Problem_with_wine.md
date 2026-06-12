---
title: "Problem with wine"
date: 2009-06-15
forum: General Help
---

### Post by Hoodline on 2009-06-15
i had wine yesterday working ok but i wanted to remove windows so i just formated my harddrive and reinstalled ubuntu by its self i have installed wine and i just installed a program but when i goto the menu its not there i have searched google for answers but there not answers to my question or complety the wrong answers i tried a few of the answered posted by other people that i found on google but its still not working or not what i want i'd *appreciate* it if anyone can help thanks

---

### Post by Hoodline on 2009-06-15
i hate to be a pain in the **** and double posting as i have looked on other sites and i havnt found nothing to solve the problem i have reinstalled wine and it still doesnt show the menu

---

### Post by 4Orbs on 2009-06-15
You need to configure wine (the first time, only) before installing any programs. When you first open the configuration manager, wine creates the folder, etc. required for it to work correctly. Even after it's set up, sometimes you need to log out and back in after installing a program or game, for that thing to show up on your wine menu. Did you check your menu under the "Other" heading. That's where wine lists its programs on my Ubuntu.

---

### Post by Hoodline on 2009-06-15
Thanks for the reply i logged out and logged back in and its still isnt there and there is nothing inside other

---

### Post by 4Orbs on 2009-06-15
If you haven't configured wine after installing, then open a terminal and enter winecfg and that should open the wine settings mgr. Then click on apply and close (without changing any configuration settings). Then log out and back in. That should set up your hidden .wine folder. You can check it is there by opening the file mgr (Nautilus) and in the Nautilus "View" menu select "Show Hidden Files". Then in your personal home directory look for the .wine folder. If it's there, then you can open it up and look under "Drive C" and see if the program you installed has a folder inside the "Program Files" directory. If that program is there, you can double click on the program .exe file start the program. But before double clicking the .exe file, right-click on it and select the Properties option, then select the option to "Open with Wine Program Loader" so wine will open .exe files rather than the Archive Mgr trying to open them.

---

### Post by Hoodline on 2009-06-15
Its creates the wine folder but not the menu

---

### Post by 4Orbs on 2009-06-15
The Drive C folder and DOS Devices folder were also created?? Inside the drive_c folder is the Program Files folder. If the new app you installed is not inside the Program Files folder, then you should install that app again, then make sure it has a folder inside Program Files. If installing the app does create its folder inside Program Files, then the app should show up on the wine menu. May need a reboot or logout first.

EDIT: You also may need to open the winecfg again and select the audio driver, apply and save. The other options worked fine at default settings for me. But you might take a look at them.

---

### Post by Hoodline on 2009-06-15
Yes the c folder and dos folder are there but when i select the audio tab i get this in terminal

```

err:module:load_builtin_dll failed to load .so lib for builtin L"winearts.drv": libartsc.so.0: cannot open shared object file: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack

```

---

### Post by nolliecrooked on 2009-06-15
> **Hoodline said:**
> Yes the c folder and dos folder are there but when i select the audio tab i get this in terminal

```

err:module:load_builtin_dll failed to load .so lib for builtin L"winearts.drv": libartsc.so.0: cannot open shared object file: No such file or directory
fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack

```

why the hell is it trying to load the Jack driver?

did you set it to use the Jack driver in the Wine Config Audio tab?

---

### Post by Hoodline on 2009-06-15
No all i did is clicked the audio tab and i got that message

---

### Post by nolliecrooked on 2009-06-15
> **Hoodline said:**
> No all i did is clicked the audio tab and i got that message

try running;

sudo aptitude install libjack0

in Terminal, and see if it helps

---

### Post by Hoodline on 2009-06-15
Thanks for your help but i still get the same message

---

### Post by nolliecrooked on 2009-06-15
> **Hoodline said:**
> Thanks for your help but i still get the same message

no probs man, sorry I cant help ya more.

---

### Post by Hoodline on 2009-06-15
do you know of anything else like wine to run windows apps and games?

---

### Post by nolliecrooked on 2009-06-15
> **Hoodline said:**
> do you know of anything else like wine to run windows apps and games?

yea. theres Crossover Games;

[http://www.codeweavers.com/products/cxgames/](http://www.codeweavers.com/products/cxgames/)

or Cedega;

[http://www.codeweavers.com/products/cxgames/](http://www.codeweavers.com/products/cxgames/)

they both cost though, and I dunno if the Jack issue would affect them too, as their both based off WINE.

---

### Post by Hoodline on 2009-06-15
ok thanks i just dont understand why its doing this it worked fine yesterday it just started acting strange after i reinstalled ubuntu

---

### Post by 4Orbs on 2009-06-16
If I understand correctly, you originally installed Ubuntu inside Windows using a Wubi install. Then you completely wiped windows and installed a fresh Ubuntu as the only os on your computer.

1. You need to run the Update Manager first and wait while it installs the updates.
2. Then you should go to Hardware Drivers Mgr and activate the driver for your graphics card.
3. Then you need to get your multimedia stuff working by following the Comprehensive Multi Media and Video how-to (sticky thread in the multimedia section of this forum).
4. Then you open Synaptic Package Mgr and install wine.
5. Then configure wine by opening the Wine Config Settings Mgr by entering in a terminal winecfg and select the proper audio driver (probably Alsa, but if using old computer maybe select OSS driver instead.
6. If all the above worked with no errors, now you can install a Windows program into wine, but first be sure the .exe file is set to be opened with the Wine Program loader.

If you didn't set up your new Ubuntu installation in this order, but you did do all the steps (in a different order), then I believe you can just open Synaptic Package Mgr and mark Wine for re-installation and after it reinstalls configure it again as above, and try installing your Windows program again. Don't know, but I suspect the problem you have now is because you installed the Windows program before you had done the initial set-up of wine.

---

### Post by cottfcfan on 2009-06-16
May be just a coincidence, but i did a reinstall yesterday, and also had a problem with wine from the repositories.
 Drove me mad. In the end i uninstalled it, and reinstalled from the wine website, through the terminal. I also installed my wine programs using the terminal and all was fine.
 Strange, no idea what the problem was, but try it, it might work.

---

