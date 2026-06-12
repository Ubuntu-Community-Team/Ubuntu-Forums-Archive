---
title: "Compiz/Ubuntu-Tweaks settings gone after updating"
date: 2013-04-24
forum: Desktop Environments
---

### Post by zelgit on 2013-04-24
Hi this is my first post here. I have **Ubuntu 12.04** LTS via **Wubi**.

The problem is that my settings were changed back to default or something after I did all the updates that the Update Manager wanted, including the **latest** **xorg** and **X11** **updates**.

**My settings were as follows:**
1. Wobbling windows (Compiz)
2. Snapping windows (like in Windows 7, also in Compiz)
3. Hot corners (Ubuntu Tweaks)
4. Changing icon size in Launcher (Ubuntu Tweaks/Compiz)

**Problem with the above:**
1. Doesn't take effect
2. Gone from the old place I guess
3. Gone from the old place
4. Doesn't take effect

Thanks in advance!

---

### Post by zelgit on 2013-04-24
Ok **I solved it** myself! **Here is the solution **(as for me):

1. Uninstalled complete Compiz by:
**sudo apt-get uninstall compiz***

** I think this deleted my Unity as well

2. Reinstalled complete Compiz by:
**sudo apt-get install compiz***

** HOWEVER, this took alot of time to download and install and I don't think you should do this. Maybe you only should install the parts you need from Compiz

3. Apparently the Update Manager deleted my current Nvidia driver and when I rebooted I had some standard driver. Therefore I reinstalled the latest Nvidia driver like this:

     3.0. Download your driver from Nvidia Driver site:  [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)
            and save it somewhere you know.
     3.1. In Ubuntu press these buttons:** Ctrl + Alt + F1 **
     3.2. Run: **sudo service gdm stop** (Ubuntu 11.04 or earlier) 
     3.2. OR Run: **sudo service lightdm stop **(Ubuntu 11.10 or newer) 
     3.3. Navigate to the .run-file you saved in a place you know
     3.4. Run the installation with this: **sudo sh ***<name of the.run-file>*
     3.5. Go through the installation and reboot by: **sudo reboot**

4. When have rebooted there is not Unity bar or launcher. Install Unity and run it!

    4.1. Open Terminal and type: **sudo apt-get install unity**
    4.2. In the same Terminal type only this to run it: **unity**

Now everything is working again, so I hope this will help others as well. If it please type it here if you have time :)

Cheers!

---

