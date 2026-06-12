---
title: "How to automatically set the brightness when the laptop starts up"
date: 2013-06-22
forum: Desktop Environments
---

### Post by freedommakeperfect on 2013-06-22
I have put some words in the "GOOGLE" and search for some resolutions about this question, so do the forum. 
However, it seems that they have no effect on the brightness adjustment when the system starts up. 
I don't why i can't succeed  in setting the lightness on start-up. My environment desktop is LXDE. The video card is amd.

Maybe I'm so stupid and do something wrongly.

Here is my efforts:
I tried to install the laptop-mode-tools in my lubuntu, and **sudo vi /etc/laptop-mode/laptop-mode.conf **, 
then **ENABLE_LAPTOP_MODE_ON_AC=1**.
Next, I sudo  vi /etc/laptop-mode/laptop-mode/conf.d/lcd-brightness.conf
revised the content in the file as follows.
```
CONTROL_BRIGHTNESS=1
BATT_BRIGHTNESS_COMMAND=”echo 3&#8243;
LM_AC_BRIGHTNESS_COMMAND=”echo 3&#8243;
NOLM_AC_BRIGHTNESS_COMMAND=”echo 3&#8243;
#BRIGHTNESS_OUTPUT=”/proc/acpi/video/VID/LCD/brightness”
BRIGHTNESS_OUTPUT=”/sys/class/backlight/acpi_video0/brightness”

```
and then saved and do **sudo update-grub**, but it seems that it doesn't work on LXDE . Is something that I do wrongly?

Then I tried some scripts on start-up. Oh, I feel crazy about it although I have tried it for many times.
It also seems that It doesn't work on LXDE.

Would you please give me ways of solving the problems or point out which step I do is wrong? :)

---

### Post by lisati on 2013-06-22
*Thread moved to **Desktop Environments**.*

---

### Post by victor-9 on 2014-02-03
Here is what I did :

In : /home/user/.config/autostart 
open the "Set brightness" file with a text editor, you should see :

```
[Desktop Entry]
Type=Application
Exec=xbacklight -set **40**
Hidden=false
NoDisplay=false
X-GNOME-Autostart-enabled=true
Name[en_US]=Set brightness
Name=Set brightness
Comment[en_US]=
Comment= 
```

Just change the value "40" at your convenience

---

