---
title: "Xubuntu 14.04 cannot change wallpaper"
date: 2014-06-29
forum: Desktop Environments
---

### Post by dentaku65 on 2014-06-29
Hi,

I've upgrade from 13.10 to 14.04 xubuntu and I'm not able to change wallpaper via Desktop Settings; no matter which folder I choose (personal wallpapers folder or /usr/share/xfce4/backdops), click the chosen picture the setting wont apply and even the style does nothing (centered, zoomed, scaled and so on).

The only way to change wallpaper on my box is via Thunar doing right click on the image and "Set as wallpaper..." option; of course with this method I'm unable to set the style of the wallpaper.

The configuration seems to me correct
```
apt-cache policy xfdesktop4
```
> xfdesktop4:
  Installed: 4.11.6-1ubuntu1
  Candidate: 4.11.6-1ubuntu1
  Version table:
 *** 4.11.6-1ubuntu1 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/universe amd64 Packages
        100 /var/lib/dpkg/status
```
ls -l $HOME/.config/xfce4/xfconf/xfce-perchannel-xml/
```
> -rw-rw-r-- 1 sava sava   212 Jun  5  2013 keyboard-layout.xml
-rw-rw-r-- 1 sava sava   204 May 19  2013 keyboards.xml
-rw-r--r-- 1 sava sava   839 Jun 11 20:48 parole.xml
-rw-rw-r-- 1 sava sava   639 Oct  1  2013 pointers.xml
-rw-rw-r-- 1 sava sava   272 May 20  2013 ristretto.xml
-rw-rw-r-- 1 sava sava  2847 Jun 29 11:34 thunar.xml
-rw-r--r-- 1 sava sava  1816 Jun 24 08:26 xfce4-appfinder.xml
-rw-rw-r-- 1 sava sava  2615 Jun 29 11:25 xfce4-desktop.xml
-rw-rw-r-- 1 sava sava 11470 May 24  2013 xfce4-keyboard-shortcuts.xml
-rw-rw-r-- 1 sava sava   262 Jun  1  2013 xfce4-mixer.xml
-rw-r--r-- 1 sava sava   311 Oct 18  2013 xfce4-notifyd.xml
-rw-rw-r-- 1 sava sava  7015 Jun 29 10:12 xfce4-panel.xml
-rw-r--r-- 1 sava sava  1509 Jan  8 19:40 xfce4-session.xml
-rw-rw-r-- 1 sava sava   336 Sep 18  2013 xfce4-settings-editor.xml
-rw-r--r-- 1 sava sava   276 Oct  6  2013 xfce4-settings-manager.xml
-rw-r--r-- 1 sava sava  4235 May 10 10:43 xfwm4.xml
-rw-rw-r-- 1 sava sava  1763 Sep 23  2013 xsettings.xml
```
ls -l $HOME/.cache/sessions
```
> drwx------ 2 sava sava 4096 Jun 28 11:44 thumbs-sava-new:0
-rw-rw-r-- 1 sava sava 2428 Jun 29 10:03 xfce4-session-sava-new:0
-rw-rw-r-- 1 sava sava 2428 Jun 29 09:14 xfce4-session-sava-new:0.bak

Does anybody have some hints?

TIA
Den

---

### Post by Toz on 2014-06-29
What video card do you have and what driver are you using?
```
lspci -k | grep -A2 VGA
```

What are your xfdesktop settings? The following command will display them:
```
xfconf-query -c xfce4-desktop -lv
```

Also, run the following command, and then try to change the wallpaper via Desktop Settings, and then via Thunar. Post back what displays in the terminal window. Lets see which xfconf keys are being affected with each method:
```
xfconf-query -c xfce4-desktop -m
```

There was a bug during the beta cycle in which the desktop settings applet was writing to the wrong xfconf key. This was supposedly fixed but maybe somehow you're still being affected.

---

### Post by dentaku65 on 2014-06-29
> **Toz said:**
> What video card do you have and what driver are you using?
```
lspci -k | grep -A2 VGA
```

What are your xfdesktop settings? The following command will display them:
```
xfconf-query -c xfce4-desktop -lv
```

Also, run the following command, and then try to change the wallpaper via Desktop Settings, and then via Thunar. Post back what displays in the terminal window. Lets see which xfconf keys are being affected with each method:
```
xfconf-query -c xfce4-desktop -m
```

There was a bug during the beta cycle in which the desktop settings applet was writing to the wrong xfconf key. This was supposedly fixed but maybe somehow you're still being affected.

Hi Toz,

here the outputs

```
lspci -k | grep -A2 VGA
```
> 00:01.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7400G]
	Subsystem: Samsung Electronics Co Ltd Device c660
	Kernel driver in use: fglrx_pci
```
xfconf-query -c xfce4-desktop -lv
```
> /backdrop/screen0/monitor0/image-path                            /home/sava/Pictures/wallpaper/_image.jpg.png
/backdrop/screen0/monitor0/image-show                            true
/backdrop/screen0/monitor0/image-style                           0
/backdrop/screen0/monitor0/last-image                            /home/sava/Pictures/wallpaper/_image.jpg.png
/backdrop/screen0/monitor0/last-single-image                     /home/sava/Pictures/wallpaper/_image.jpg.png
/backdrop/screen0/monitor0/workspace0/last-image                 /home/sava/Pictures/wallpaper/image.jpg.png
/backdrop/screen0/monitor1/image-path                            /home/sava/Pictures/wallpaper/image.jpg.png
/backdrop/screen0/monitor1/image-show                            true
/backdrop/screen0/monitor1/image-style                           5
/backdrop/screen0/monitorLVDS/workspace0/color-style             0
/backdrop/screen0/monitorLVDS/workspace0/image-style             3
/backdrop/screen0/monitorLVDS/workspace0/last-image              /home/sava/Pictures/wallpaper/_image.jpg.png
/backdrop/screen0/monitorLVDS/workspace-1/backdrop-cycle-enable  false
/backdrop/screen0/monitorLVDS/workspace-1/image-style            5
/backdrop/screen0/monitorLVDS/workspace-1/last-image             /home/sava/Pictures/wallpaper/image.jpg.png
/backdrop/single-workspace-mode                                  true
/backdrop/single-workspace-number                                -1
/desktop-icons/file-icons/show-filesystem                        false
/desktop-icons/file-icons/show-home                              true
/desktop-icons/file-icons/show-removable                         true
/desktop-icons/file-icons/show-trash                             false
/desktop-icons/icon-size                                         42
/desktop-icons/style                                             2
/last/window-height                                              511
/last/window-width                                               646
```
xfconf-query -c xfce4-desktop -m
```
> set: /backdrop/screen0/monitorLVDS/workspace-1/last-image
set: /backdrop/screen0/monitorLVDS/workspace-1/last-image
set: /backdrop/screen0/monitorLVDS/workspace-1/last-image
This last output is quite weird, not matter what image I choose, the wallpaper do not change.

kr,
den

---

### Post by Toz on 2014-06-29
> **dentaku65 said:**
> >  set: /backdrop/screen0/monitorLVDS/workspace-1/last-image
set: /backdrop/screen0/monitorLVDS/workspace-1/last-image
set: /backdrop/screen0/monitorLVDS/workspace-1/last-image 
This last output is quite weird, not matter what image I choose, the wallpaper do not change.

Which method generated these results? The Thunar method? If so, what does the Desktop Settings method generate? Or vice versa.

---

### Post by dentaku65 on 2014-06-29
> **Toz said:**
> Which method generated these results? The Thunar method? If so, what does the Desktop Settings method generate? Or vice versa.

The output posted was generated via Desktop Settings; via Thunar generate this one:
> set: /backdrop/screen0/monitor0/image-path
set: /backdrop/screen0/monitorLVDS/workspace0/last-image
that seems correct to me.

Do you have any idea what was the wrong xfconf key in the desktop settings applet in the beta cycle?

---

### Post by Toz on 2014-06-29
I don't remember exactly, other than it was writing to the the wrong xfconf entry (I'll see if I can dig up the bug report). The same is happening with your system:

- It looks like thunar is writing to: /backdrop/screen0/monitor0/image-path
- And desktop settings to: /backdrop/screen0/monitorLVDS/workspace-1/last-image

Can you try the following to reset the desktop xfconf settings to defaults (**note, you will lose all the settings in the desktop settings applet)?
1. Log out 
2. Go to a text terminal (Ctrl+Alt+F1)
3. Log in to the text terminal. 
4. Rename the desktop xfconf xml file:
```
cd ~/.config/xfce4/xfconf/xfce-perchannel-xml
mv xfce4-desktop.xml xfce4-desktop.xml.BAK
```
5. Return to the gui login screen (Ctrl+Alt+F7)
6. Log back in again.
7. Perform the same tests from my post #2 again. See if it makes any difference.

---

### Post by dentaku65 on 2014-06-30
Hi,

thank tou very much.
Removing xfce4-desktop.xml and rebooting the box fixed my issue; a new xfce4-desktop.xml has been recreated with the default wallpaper, changing the wallpaper via Desktop Settings works fine now with the styles too.

Solved.

---

