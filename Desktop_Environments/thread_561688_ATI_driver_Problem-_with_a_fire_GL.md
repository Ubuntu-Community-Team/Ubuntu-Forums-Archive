---
title: "ATI driver Problem- with a fire GL"
date: 2007-09-27
forum: Desktop Environments
---

### Post by soulence on 2007-09-27
I have a laptop that has a firegl card in it i think its a FireGL 5200 or 52xx and after installing the ati driver it works fine still fast but when i go to do the beryl walk through after editing my xorg.conf i crash and have the whole x did not load.

So instead of trying to edit it i reinstalled and it did it again and again about 3 times as each time x failed to restart and i cant find much info on FIREGL IN Linux or UBUNTU  


ANy help?

---

### Post by w4ett on 2007-09-29
Here is a thread on that chipset:

[http://ubuntuforums.org/showthread.php?t=305764](http://ubuntuforums.org/showthread.php?t=305764)

If X wont start, try reconfiguring your xorg.conf:

boot into recovery mode.

From the command line type:


```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select [COLOR="Red"]"vesa" or "ati"[/COLOR] as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:


```
startx
```

---

