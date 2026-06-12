---
title: "Ubuntu 12.04 LTS on Dell XPS 14z - temperature, touchpad and other issues"
date: 2013-03-20
forum: Dell Ubuntu Support (CLOSED)
---

### Post by samuelcersosimo on 2013-03-20
This is my first thread in Ubuntu Forums and it is a work in progress. I hope that you can help me improve this list, especially on the solutions and workarounds that I found for temperature and battery consumption on the **Dell XPS 14z (L412z)** notebook, while running **Ubuntu 12.04 LTS (Precise Pangolin)**.

I accept any corrections and suggestions.

**For beginners: **
- The [COLOR=#0000FF]blue[/COLOR] tips are command lines that should be executed in Terminal (type 'Ctrl + Alt + T' to open the Terminal).
- You can copy and paste on the Terminal (use 'Shift + Insert' instead of 'Ctrl + V').
- The "$" symbol should not be copied.


[COLOR=#008000][B]*** TEMPERATURE ISSUE AND BATTERY LIFE ON DELL XPS 14Z WITH UBUNTU 12.04 LTS ***
[/B][/COLOR]
After these tweaks, the CPU temperature will run in about 40 up to 48ºC with regular use (this is OK), and up to 80ºC when gaming (my alarm is set to 85ºC). The HDD temperature will decrease to 36 up to 41ºC.

[COLOR=#b22222]**1. Install and configure lm-sensors and cpufrequtils:**[/COLOR]
[COLOR=#0000ff]$ sudo apt-get install lm-sensors cpufrequtils indicator-cpufreq
$ sudo sensors-detect[/COLOR]
(confirm all options with "y")

[COLOR=#b22222]**2. Install Psensor to keep track of your CPU and HD temperature:**[/COLOR]
[COLOR=#0000ff]$ sudo apt-get install psensor[/COLOR]
(choose to activate "hddtemp" on boot when asked)

- After install it will execute automaticaly on system startup. 
- You can block it on the launcher to see it permanently (the launcher icon has a neat temperature indicator).

[COLOR=#b22222]**3. Install Jupiter to manage battery consumption:**[/COLOR]
[COLOR=#0000ff]$ sudo add-apt-repository ppa:webupd8team/jupiter && sudo apt-get update
$ sudo apt-get install jupiter[/COLOR]

[COLOR=#b22222]**4. Install Bumblebee to manage battery consumption and the use of the nVIDIA GPU when needed (use "optirun" before the application name to open with nVIDIA GPU):**[/COLOR]
[COLOR=#0000ff]$ sudo add-apt-repository ppa:bumblebee/stable && sudo apt-get update
$ sudo apt-get install bumblebee[/COLOR]

- Test and compare:
[COLOR=#0000ff]$ glxspheres
$ optirun glxspheres[/COLOR]

[COLOR=#b22222]**5. To decrease Hard Disk temperature (the unconfortable heating on your left palm hand, where the HDD hardware is set), you will have to install laptop-mode-tools and follow the instructions on the link below:**[/COLOR]
[COLOR=#0000ff]$ sudo apt-get install laptop-mode-tools[/COLOR]

- Edit laptop-mode.conf file: 
[COLOR=#0000ff]$ sudo gedit /etc/laptop-mode/laptop-mode.conf[/COLOR]

- Find the bellow text and change value to **600**:
[COLOR=#0000ff]NOLM_HD_IDLE_TIMEOUT_SECONDS=7200[/COLOR]

- Find the bellow texts and change both values to **1**:
[COLOR=#0000ff]LM_AC_HD_POWERMGMT=254[/COLOR]
[COLOR=#0000ff]NOLM_AC_HD_POWERMGMT=254[/COLOR]

- Refers to:
[http://askubuntu.com/questions/141343/hard-drive-overheats-when-laptop-running-on-ac-power](http://askubuntu.com/questions/141343/hard-drive-overheats-when-laptop-running-on-ac-power)

[COLOR=#b22222]**6. Use Powertop (from Intel) software to tweak some power consumption settings:**[/COLOR]
[COLOR=#0000ff]$ sudo apt-get install powertop
$ sudo powertop --calibrate[/COLOR]
(wait)
[COLOR=#0000ff]$ sudo powertop[/COLOR]
(change "Bad" values to "Good" using keyboard arrows and 'Enter'. Type 'Esc' when finished.) **-- this is not 100% tested**.

[COLOR=#b22222]**7. Those above are the easiest tips that I've found. To go more deep, you can refer the links bellow and, later, post here what you accomplished:**[/COLOR]
[http://smackerelofopinion.blogspot.com.br/2011/12/improving-battery-life-in-ubuntu.html](http://smackerelofopinion.blogspot.com.br/2011/12/improving-battery-life-in-ubuntu.html)
[http://smackerelofopinion.blogspot.com.br/2012/01/improving-battery-life-in-ubuntu.html](http://smackerelofopinion.blogspot.com.br/2012/01/improving-battery-life-in-ubuntu.html)


[COLOR=#008000][B]*** TOUCHPAD SENSIBILITY ISSUE ON DELL XPS 14Z WITH UBUNTU 12.04 LTS ***
[/B][/COLOR]
The mouse pointer keeps shaking and jumping on the screen when I use touchpad on my Dell XPS 14z, especially in cold rooms. It's horrible! These are some tweaks that I tryied with the synclient software, that manages the Synaptics driver (responsible for touchpad in Ubuntu 12.04). Try some of those an let me know if it worked for you.

[COLOR=#b22222]**1. Ultimately, I've had success by changing the HorizHysteresis and VertHysteresis values on the synclient for 48. Do this:**[/COLOR]
- Check the current value (should be 8):
[COLOR=#0000ff]$ synclient | grep HorizHysteresis && synclient | grep VertHysteresis [/COLOR]

- Change value to 72 on each (first I tried 48, with goog results also):
[COLOR=#0000ff]$ synclient HorizHysteresis=72 && synclient VertHysteresis=72[/COLOR]

- These tweaks will be lost after system restart. To make the changes permanent, you'll have to create and edit a xorg.conf file. Do this:
[COLOR=#0000ff]$ sudo gedit /etc/X11/xorg.conf[/COLOR]

- It will open a blank text file. Insert the following content and save:
[COLOR=#0000FF]
Section "InputClass"[/COLOR]
[COLOR=#0000ff]     Identifier              "Touchpad"
     Driver                  "synaptics"
     MatchIsTouchpad    "on"
     Option         "VertHysteresis"    "72"
     Option         "HorizHysteresis"   "72"
EndSection[/COLOR]

- For more options on xorg.conf file, refer to:
[http://askubuntu.com/questions/130217/how-to-edit-synaptics-touchpad-values-in-ubuntu-12-04-no-xorg-conf-file](http://askubuntu.com/questions/130217/how-to-edit-synaptics-touchpad-values-in-ubuntu-12-04-no-xorg-conf-file) and
[https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Frequently_used_options](https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Frequently_used_options)

[COLOR=#b22222]**2. Other tweaks that I've tried before (with less success) was changing the FingerLow, FingerHigh and FingerPress values with the above commands:**[/COLOR]
- First, check the FingerLow, FingerHigh and FingerPress current values with the above command:
[COLOR=#0000ff]$ synclient | grep FingerLow && synclient | grep FingerHigh && synclient | grep FingerPress[/COLOR]

- You will probably get:
[COLOR=#0000ff]FingerLow = 25
FingerHigh = 30
FingerPress = 256[/COLOR]

- Try decreasing FingerLow and increasing FingerHigh values (I actually didn't try to change FingerPress values becouse the HorizHysteresis and VertHysteresis tweaking showed to be the better solution). To change any value, do such as:
[COLOR=#0000ff]$ synclient FingerLow=20
$ synclient FingerHigh=50[/COLOR]

Refer to:
[http://askubuntu.com/questions/128023/synaptics-touchpad-sensitivity-issue](http://askubuntu.com/questions/128023/synaptics-touchpad-sensitivity-issue)

For more settings on Synaptics driver, refer to:
[http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html](http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html)

[COLOR=#b22222]**3. Enable two fingers scrolling in System Settings > Mouse and Touchpad > Touchpad (this is optional)**[/COLOR]


[COLOR=#008000][B]*** OTHER THINGS THAT I DO AFTER INSTALLING UBUNTU 12.04 LTS ON MY DELL XPS 14Z ***
[/B][/COLOR]
This is my personal check-list, but it has some cool tips.

[COLOR=#b22222]**1. Install Java (necessary for internet banking):**[/COLOR]
[COLOR=#0000ff]$ sudo apt-get install openjdk-7-jre icedtea-plugin[/COLOR]
(resolve problema do Banco do Brasil no Ubuntu / funciona para o Mozilla Firefox) **-- this is a tip for my brazilian fellows**.

[COLOR=#b22222]**2. Install ubuntu restricted extras package:**[/COLOR]
[COLOR=#0000ff]$ sudo apt-get install ubuntu-restricted-extras[/COLOR]

[COLOR=#b22222]**3. Show global menu in LibreOffice:**[/COLOR]
[COLOR=#0000ff]$ sudo apt-get install lo-menubar[/COLOR]

[COLOR=#b22222]**4. Improve clipboard (copy and paste between apps even after closing the previous one):**[/COLOR]
[COLOR=#0000ff]$ sudo apt-get install parcellite
[/COLOR]
- To make it run on system startup, go to settings (cog in the top right of your desktop screen in Unity) and click on Startup Applications. Then click 'Add' and write "parcellite" on the two first fiels. Confirm.

[COLOR=#b22222]**5. Reduce font size, Launcher appearence and put a Show Desktop Icon on the Launcher:**[/COLOR]
[COLOR=#0000ff]$ sudo apt-get install myunity[/COLOR]

- On Font, set font sizes -1 of the current.
- On Launcher, set Backlights as 'Active Icons Only'.
- On Desktop, set Active "Show Desktop" icon as ON.

[COLOR=#b22222]**6. Install the best app to backup personal files, usb drives and external drives (FreeFileSync):**[/COLOR]
[COLOR=#0000ff]$ sudo add-apt-repository ppa:freefilesync/ffs && sudo apt-get update
$ sudo apt-get install freefilesync[/COLOR]

[COLOR=#b22222]**7. Install Radio Tray Indicator (I recomend the "CINEMIX" radio):**[/COLOR]
[COLOR=#0000ff]$ sudo add-apt-repository ppa:eugenesan/ppa && sudo apt-get update
$ sudo apt-get install radiotray[/COLOR]

- For other great indicators, refere to:
[http://maketecheasier.com/10-must-have-indicator-applets-for-ubuntu-12-04/2012/06/15](http://maketecheasier.com/10-must-have-indicator-applets-for-ubuntu-12-04/2012/06/15)

[COLOR=#b22222]**8. Creating a keyboard shortcut to open files and directories (Nautilus) - Similar to 'Super + E' on Microsoft Windows:**[/COLOR]
Go to System Settings > Keyboard > Keyboard Shortcuts > Launchers > click 'Personal Folder' and type 'Ctrl + Alt + A' on your keyboard.

[COLOR=#b22222]**9. Install Storage Device Manager and configure particions to mount on boot:**[/COLOR]
[COLOR=#0000ff]$ sudo apt-get install pysdm[/COLOR]

[COLOR=#b22222]**10. Speed up Ubuntu**[/COLOR]
- Watch: [http://youtu.be/vwBoHZuauL8](http://youtu.be/vwBoHZuauL8)

[COLOR=#b22222]**11. Disable/remove overlay scrollbars:**[/COLOR]
[COLOR=#0000ff]$ [/COLOR][COLOR=#0000ff]gsettings set org.gnome.desktop.interface ubuntu-overlay-scrollbars false[/COLOR]

[COLOR=#008000][B]*** REFERENCES TO ***
[/B][/COLOR]
[http://handytutorial.com/install-freefilesync-in-ubuntu-12-10-12-04-using-ppa/](http://handytutorial.com/install-freefilesync-in-ubuntu-12-10-12-04-using-ppa/)
[http://thedaneshproject.com/posts/how-to-install-java-7-on-ubuntu-12-04-lts/](http://thedaneshproject.com/posts/how-to-install-java-7-on-ubuntu-12-04-lts/)
[http://www.webupd8.org/2012/04/things-to-tweak-after-installing-ubuntu.html](http://www.webupd8.org/2012/04/things-to-tweak-after-installing-ubuntu.html)
[http://askubuntu.com/questions/141343/hard-drive-overheats-when-laptop-running-on-ac-power](http://askubuntu.com/questions/141343/hard-drive-overheats-when-laptop-running-on-ac-power)
[http://askubuntu.com/questions/128023/synaptics-touchpad-sensitivity-issue](http://askubuntu.com/questions/128023/synaptics-touchpad-sensitivity-issue)
[http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html](http://www.x.org/archive/X11R7.5/doc/man/man4/synaptics.4.html)
[https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/992330](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/992330)
[http://askubuntu.com/questions/130217/how-to-edit-synaptics-touchpad-values-in-ubuntu-12-04-no-xorg-conf-file](http://askubuntu.com/questions/130217/how-to-edit-synaptics-touchpad-values-in-ubuntu-12-04-no-xorg-conf-file)
[https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Frequently_used_options](https://wiki.archlinux.org/index.php/Touchpad_Synaptics#Frequently_used_options)
[http://smackerelofopinion.blogspot.com.br/2011/12/improving-battery-life-in-ubuntu.html](http://smackerelofopinion.blogspot.com.br/2011/12/improving-battery-life-in-ubuntu.html)
[http://smackerelofopinion.blogspot.com.br/2012/01/improving-battery-life-in-ubuntu.html](http://smackerelofopinion.blogspot.com.br/2012/01/improving-battery-life-in-ubuntu.html)

---

