---
title: "Beryl + ATI Radeon 9600 problem"
date: 2007-05-19
forum: Desktop Effects &amp; Customization
---

### Post by anarchitecton on 2007-05-19
Hello.

I used the following tutorial to install beryl+ubuntu 7.04+ ATI Radeon 9600:  

**[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")**

After completing it, everything seemed to work fine... well at least the effects.

Unfortunately some corruption occurs in the form of strange lines and artifacts when moving/clicking things around.

here's a screenshot:
[[IMG]http://img257.imageshack.us/img257/5444/screenshotqk1.th.png[/IMG]](http://img257.imageshack.us/my.php?image=screenshotqk1.png)

Anyone had similar problems and was able to solve it?

Thanks in advance.

---

### Post by ericallen on 2007-05-20
hello, after much headache and trying out all sorts of different things I got it working good
I followed that same tutorial and also have an ati-9600 (and amd64 processor)

{UPDATE}
I completely reinstalled ubuntu to try and figure out how I got it working, and it was **Envy**[http://www.albertomilone.com/nvidia_scripts1.html]("http://www.albertomilone.com/nvidia_scripts1.html") I used Envy to install the ati driver (reboot system) and then used Envy again to *uninstall *the driver; then reboot again

then run in Terminal
```
sudo dpkg-reconfigure xserver-xorg
```
this will ask a series of questions about your hardware and it'll rebuild the xorg.conf 
REBOOT
afterwards when I click the Restricted Drivers Manager it says:
> Your hardware does not need any restricted drivers
then I removed Envy

then go do the tutorial [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon]("http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon")
.............................
It will take some time to figure out what works best for your system, but in the end the eye-candy is worth it
I also set my default display depth to 16, I don't know if that would help but it's worth a try

just for kicks here's some glxgears output while running beryl
13195 frames in 5.0 seconds = 2638.890 FPS
13093 frames in 5.0 seconds = 2618.478 FPS
12946 frames in 5.0 seconds = 2589.046 FPS
while holding ctrl+alt+right (spinning cube)
2698 frames in 5.0 seconds = 539.568 FPS
2588 frames in 5.0 seconds = 517.308 FPS
2202 frames in 5.0 seconds = 440.315 FPS
window maximized
1403 frames in 5.0 seconds = 280.410 FPS
1384 frames in 5.0 seconds = 276.514 FPS
1290 frames in 5.0 seconds = 257.985 FPS

and in gnome not running beryl
17912 frames in 5.0 seconds = 3582.328 FPS
17915 frames in 5.0 seconds = 3582.809 FPS
17914 frames in 5.0 seconds = 3582.780 FPS

---

