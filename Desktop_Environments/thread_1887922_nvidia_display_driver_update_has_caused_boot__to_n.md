---
title: "nvidia display driver update has caused boot  to non functional desktop"
date: 2011-11-28
forum: Desktop Environments
---

### Post by james2b on 2011-11-28
I have Ubuntu 11.10 Unity all updated, and I just did a nvidia display driver update, which has caused it to now boot to a non functional desktop. I have mouse cursor function to click on things but then nothing happens, so there is no function, I can only see the desktop items but nothing happens when clicked on. So I did try that boot into the Recovery Mode, and some commands run in the run level 3 console. I had nvidia driver version 173 that did work fine, but when attempted version current it broke it. So how can I un-install or remove that NVIDIA display driver ? I do have a copy of my file; /etc/X11/xorg.conf, but how can I edit that file from a console command ?

---

### Post by randywilharm on 2011-11-28
> **james2b said:**
> I have Ubuntu 11.10 Unity all updated, and I just did a nvidia display driver update, which has caused it to now boot to a non functional desktop. I have mouse cursor function to click on things but then nothing happens, so there is no function, I can only see the desktop items but nothing happens when clicked on. So I did try that boot into the Recovery Mode, and some commands run in the run level 3 console. I had nvidia driver version 173 that did work fine, but when attempted version current it broke it. So how can I un-install or remove that NVIDIA display driver ? I do have a copy of my file; /etc/X11/xorg.conf, but how can I edit that file from a console command ?


I don't know what you have for an nvidia card, but "version 173" sounds
pretty old...you should get a new one from here:

[http://www.nvidia.com/Download/index.aspx?lang=en-us]("http://www.nvidia.com/Download/index.aspx?lang=en-us")


ALSO (and you can do this anytime)
Try resetting X server:

sudo dpkg-reconfigure -phigh xserver-xorg

.

---

### Post by james2b on 2011-11-28
The computer with this issue is a 2006 Gateway with a nvidia GeForce 7300 GS video card also from 06. I can only do anything from the run level 3 console mode, so it would be rather hard to get that NVIDIA driver downloaded and installed all by commands ? I will try that resetting the X server from console. I had the 11.04 Ubuntu installed and working with that nvidia 173 driver version, then I did a upgrade to the 11.10 which used that same display driver version, and it worked fine but wanted to try the newer version current driver. Since I have several other Linux in this multi-boot system, can I just boot to one of my other Linux to mount the 11.10 partition, then edit this file; /etc/X11/xorg.conf for section "Device" under driver to remove "nvidia" and replace with a basic display ?

---

### Post by james2b on 2011-11-29
If I use apt-get remove, to uninstall the current NVIDIA display driver, I need to find out the exact name of that package, right? So how can I do that in run level 3 console mode ?

---

### Post by typhoon_tip on 2011-11-29
> **james2b said:**
> If I use apt-get remove, to uninstall the current NVIDIA display driver, I need to find out the exact name of that package, right? So how can I do that in run level 3 console mode ?

Type:
```
sudo apt-get remove nvidia
```

... and press TAB twice (no ENTER), it will show you all the options that you have.

---

### Post by heldal on 2011-11-29
> **james2b said:**
> I have Ubuntu 11.10 Unity all updated, and I just did a nvidia display driver update, which has caused it to now boot to a non functional desktop. I have mouse cursor function to click on things but then nothing happens, so there is no function, I can only see the desktop items but nothing happens when clicked on. So I did try that boot into the Recovery Mode, and some commands run in the run level 3 console. I had nvidia driver version 173 that did work fine, but when attempted version current it broke it. So how can I un-install or remove that NVIDIA display driver ? I do have a copy of my file; /etc/X11/xorg.conf, but how can I edit that file from a console command ?

Recent drivers from NVIDIA (versions 290.06 and 290.10) do not work properly or at all with several older mobile GPUs ([67]xxxGo).

[http://www.nvnews.net/vbulletin/showthread.php?t=168305](http://www.nvnews.net/vbulletin/showthread.php?t=168305)

You may check what version you have installed using the command:

```
dpkg -l "*nvidia*" | egrep "^i"
```

(list all packages with nvidia in the name, picking only those with status installed)

You may edit the X-server config on the console using a simple editor like pico. Your best option is probably to revert to the free driver temporarily so that you are able to access and use the GUI-tools to downgrade the proprietary nvidia driver.

---

### Post by james2b on 2011-11-30
Okay thanks for that insight, I will try some when home tonight. What is the built in generic free display driver called in the xorg.conf file ?

---

### Post by james2b on 2011-11-30
Okay this issue is now fixed, as I do have full desktop function again. When I removed the nvidia-current display driver, I then ran that dpkg -l to list the nvidia packages which showed I still had the older 173 version still installed, ( you would think that installing a newer nvidia driver version should also remove the older one ?). In that NVIDIA X server settings tool from the GUI desktop, under X Server Display, it does not show correct information, but this; "Unable to load X server configuration page", but both the video card and LCD monitor are detected. Thanks for all your help, and the Unity desktop is a memory hog, (uses about 345 MB RAM with no open applications, and the old gnome used only near 200-250 MB).

---

### Post by andreyvl on 2011-12-02
> **james2b said:**
> Okay this issue is now fixed, as I do have full desktop function again. When I removed the nvidia-current display driver, I then ran that dpkg -l to list the nvidia packages which showed I still had the older 173 version still installed, ( you would think that installing a newer nvidia driver version should also remove the older one ?). In that NVIDIA X server settings tool from the GUI desktop, under X Server Display, it does not show correct information, but this; "Unable to load X server configuration page", but both the video card and LCD monitor are detected. Thanks for all your help, and the Unity desktop is a memory hog, (uses about 345 MB RAM with no open applications, and the old gnome used only near 200-250 MB).

Hi. If I get it right, you solved the problem and you have normal desktop with nvidia drivers enabled. Can you pls describe step by step how you did this, since I have the same problem. When I log in there are only a background picture and a couple of icons on the desktop which I draged there before installing the nvidia driver.

---

### Post by james2b on 2011-12-05
Okay when booted to your not so good Ubuntu, hit these keyboard keys; ctrl, Alt, and F1 or F2, (so press 3 keys together), this will allow you to enter user name to log in run level 3 or console terminal mode, after your user name hit enter, then it should ask for a password to enter and hit enter, then type in this command to remove the nvidia driver; sudo apt-get remove nvidia, but then hit the tab key 2-3 times to show options to complete the package name which is nvidia-some name, so I used nvidia-current to remove the newer driver which will then allow you to be rolled back to an older nvidia driver version, (like for me nvidia-173), or to then install an older version. So; sudo apt-get remove nvidia-current and then hit the enter key to remove that package. And to list all your installed nvidia packages type; dpkg -l '*nvidia*', which can help select the exact package name to remove. After all this I did install some other desktop managers; [http://ubuntuguide.net/ubuntu-11-10-install-classic-gnome2-desktop-linux-mint-mate](http://ubuntuguide.net/ubuntu-11-10-install-classic-gnome2-desktop-linux-mint-mate)

---

### Post by andreyvl on 2011-12-09
ok. thanks. I'll try.

---

