---
title: "impossible to set the screen resolution to best"
date: 2012-11-08
forum: Desktop Environments
---

### Post by altobar2073 on 2012-11-08
hello

please consider i'm not english native and i'm not linux native ;)
so please talk to me in clear langage and tell me the exact command i may execute in the shell if you need more information, so that i can understand you and execute what you tell me to do. thx a lot !

system :
linux 10.04 on gnome
computer Asus X53Sv

problem :
i can't change my screen resolution
in system/preferences/screens, he gives me the choice with 800*600 and 1024*768
i know my screen recommanded definition is 1366*768 60Hz

what i tried :
- install nvidia X server Settings but it doesn't work
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

- tried this commands
```
gtf 1366 768 60
```
  that gives me > # 1368x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 85.86 MHz
  Modeline "1368x768_60.00"  85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync please note i tell 1366 and he gives me 1368

```
xrandr --newmode "1368x768_60.00"   85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync
```
with 1368 it gives me > X Error of failed request:  BadName (named color or font does not exist)
  Major opcode of failed request:  149 (RANDR)
  Minor opcode of failed request:  16 (RRCreateMode)
  Serial number of failed request:  18
  Current serial number in output stream:  18

```
xrandr --newmode "1368x768_60.00"   85.86  1368 1440 1584 1800  768 769 772 795  -HSync +Vsync
```
with 1366 it gives me nothing
```
xrandr --addmode default 1368x768_60.00
xrandr --output default --mode 1368x768_60.00
```
with 1368 it gives me > xrandr: Configure crtc 0 failed

```
xrandr --addmode default 1366x768_60.00
xrandr --output default --mode 1366x768_60.00
```
with 1366 it gives me nothing

in any case, i always go to system/preferences/screens
gives me a new choice with 1368x768

whan i try to applicate the new resolution, it gives me
> impossible to set the configuration for CRTC 72

it's the best i can reach
other solutions with xserver reset lead me to restart with reduced graphical

you can tell me what to do in order to clear anything i did bad before trying to fix this

thx for your time and your help

---

### Post by cwsnyder on 2012-11-08
Do I take it that the output of xrandr on a line by itself yields a response with 'default connected' starting the second line?  Are you using the **nouveau** driver for your laptop graphics display, or are you using the nVidia display driver for your nVidia GeForce GT 540M?  Note that there is a version of 304.64 proprietary driver which is dated 11/6/2012.

You may want to update/change your driver to the latest proprietary driver to see if that fixes your problem.

---

### Post by grahammechanical on 2012-11-08
This says that you are not using a Nvidia driver.

> You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.

When we activate the proprietary Nvidia driver we also get an Nvidia settings utility as part of the installation of the driver. Have you used the Additional Drivers utility to activate the Nvidia driver?

Keep in mind that you are using 10.04. The Nouveau (open source) driver that is the default video driver on 10.04 might not be the latest version. Is your monitor newer than 2010?

You might want to think about upgrading to 12.04. You might get newer, better drivers that way.

Regards.

---

### Post by altobar2073 on 2012-11-08
hello
thx to you two

i'm think that missed the place to put my thread
Asus X53Sv is a laptop, if i understand well english, no desktop
i bought it in 07/2010

i have to tell i used 10.04 years ago but my computeur crashed and went back to linux blocked laptop ... i came back to linux few days ago with 12.10 but i can't go on with unity or kde or gnome 3 (i tried all of them), i was too much in gnome 2.x to change that much ^^ so that i wanted to go back to 10.04

in my previous personal attempts, i had reach to the point i installed the Nvidia driver version **173**
according to cwsnyder idea, i installed the last version **304.64** (with this walk-through [http://doc.ubuntu-fr.org/nvidia.run](http://doc.ubuntu-fr.org/nvidia.run) in french but linux commands are the same;) )

in the 2 cases, i can't boot normally, he forces the session on graphically reduced configuration

i read the message telling
> (ee) no devices foundi'm thinking it's a problem to recognize the screen or the video card ?

---

### Post by cwsnyder on 2012-11-08
Definitely one or both.  Which I can't tell from what you have shown so far.

Try this to see if your video card has failed or not:```
lspci | grep VGA
```If you get a line describing your nVidia GeForce GT 540M, then that is probably OK, and you could probably use an external display with the laptop and have it recognized.

---

### Post by altobar2073 on 2012-11-08
```
lspci | grep VGA
```
> 00:02.0 VGA compatible controller: Intel Corporation Device 0116 (rev 09)
01:00.0 VGA compatible controller: nVidia Corporation Device 0df4 (rev a1)

---

### Post by cwsnyder on 2012-11-08
Umm. . . Correct me if I'm wrong, somebody out there, but that looks as if there are **two** video controllers on this laptop.  I'm stumped.

---

### Post by altobar2073 on 2012-11-08
i don't remember well but it seems to me that the screen resolution was the good one when i installed the 12.10

---

### Post by altobar2073 on 2012-11-08
the french support tells me it's because i got 2 video card on this computer
and that the intel card is strong

may i update intel drivers ?
(and if so, how ? ;) )

---

### Post by altobar2073 on 2012-11-10
i tried to install intel drivers by myself and internet help but it didn't work 

finally, i went back to 12.04 with gnome_panel_fallback to come back to visual environment i can use

i found important use of ram (60% in cash)

i used  [http://bumblebee-project.org/](http://bumblebee-project.org/)
and passed at 26% of ram used in cash

this use could exist on laptops with intel "optimum" video card used for easy tasks and nvidia for hard tasks

now i'm on 12.04 with stable video cards configuration

---

### Post by cwsnyder on 2012-11-10
You may also want to post a bug report on Launchpad as well.  [https://bugs.launchpad.net](https://bugs.launchpad.net)

---

