---
title: "Boot Splash Screen Not Centered. (HAY MODS!!!)"
date: 2009-05-17
forum: General Help
---

### Post by Don1500 on 2009-05-17
I have seen this problem in many questions on this forum, I have asked it a couple of times and I have never seen an answer.

1st part... My splash screen disapeared. No text no nothing, only "NO INPUT" on the screen.

OK, add VGA=791

Now Part 2; You got the splash screen back, but it's down and to the right of center.

I have tried alternate values for VGA= , but it really doesn't do the job. It moves it but will not center it. If you go too low it reverts to "NO INPUT" and the higher you go the closer to center you get but you never make it. 

BTW, It works fine from the live disk.

Any help will be greatly appreciated.

---

### Post by Svensk023 on 2009-05-17
what file are you editing exactly?

---

### Post by Don1500 on 2009-05-18
> **Svensk023 said:**
> what file are you editing exactly?

menu.lst, in the code below I added the second "vga=791", this relates to a screen resolution of 1024 X 768 (IIRC, I don't have the list with me.)

```
## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash vga=791

```
I've also adjusted screen resolution in startup-manager with the same results. (The resolution you set up for normal operation has no effect on the start up splash screen.)

FWIW. I have seen this same phenomenon on my laptop, but under different conditions. When I log off to go to another user the password screen is off center. And when I log back on it sometimes remains off center. Like the bottom right is off the screen.

BTW My display resolution (recommended for View Sonic 22" wide screen) is 1600 X 1050 and it will not display 800 X 600, I get "no input". Besides, at the next higher resolution the "UBUNTU" is almost the width of the screen and since it is off center it wraps around to the other side of the monitor. I can't give my lspci out put right now since I am at work, but I am using an ATI 9600 with the OSS driver.

---

### Post by Legace on 2009-05-18
Open Terminal, type in the following, and make sure the x and y values are correct.
```
sudo gedit /etc/usplash.conf
```

For example, for the resolution 1440x900, the x and y values should be:
```
# Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=1440
yres=900
```

Then save the file and close Text Editor (gedit).

Now, go to Terminal again, and type in the following:
```
sudo update-initramfs -u
```

Wait until Terminal is done, and then close the window.

Now make sure that you have a VGA=XXX value that is meant for your resolution in menu.lst. Then reboot, and you should be fine :)

---

### Post by Don1500 on 2009-05-18
> **Legace said:**
> Open Terminal, type in the following, and make sure the x and y values are correct.
```
sudo gedit /etc/usplash.conf
```

For example, for the resolution 1440x900, the x and y values should be:
```
# Usplash configuration file
# These parameters will only apply after running update-initramfs.

xres=1440
yres=900
```

Then save the file and close Text Editor (gedit).

Now, go to Terminal again, and type in the following:
```
sudo update-initramfs -u
```

Wait until Terminal is done, and then close the window.

Now make sure that you have a VGA=XXX value that is meant for your resolution in menu.lst. Then reboot, and you should be fine :)


Finally, something that sounds like an answer, I'll do this as soon as I get home. Thanks!!!
I know I can get the VGA=XXX set right in startup-manager.

---

### Post by Legace on 2009-05-18
> **Don1500 said:**
> BTW do you know where I can get a new list of the VGA=XXX values? The one I have is limited.

In Terminal:
```
sudo apt-get install hwinfo
```

Then:
```
sudo hwinfo --framebuffer
```

Find a mode that suits you (I reccomend 24bits).
For example, you could select:
```
Mode 0x0**[COLOR="Red"]3d6[/COLOR]**: 1856x1392 (+7424), 24 bits
```

The part you'll need is **[COLOR="Red"]3d6[/COLOR]** (the last 3 values)

Once you've got that part, close Terminal, open Calculator and select View -> Programming.
Make sure **HEX** is checked. Then type in 3D6. Then check **DEC**.

Now you should get a normal number, which is 982 with 3D6.

That number is the VGA code :)

---

### Post by Don1500 on 2009-05-18
Gotcha, Thanks!

Just thought of something. For the login splash, that pretty new one with the great logo, would this work also (But with another file, not uspalsh)?

---

### Post by Don1500 on 2009-05-18
Thanks to Legace!!!

I just did this and it works. Through out I used 1024X768 or 791 (16 bit) for the resolution, this worked even though my screen resolution is 1680X1050. I might try higher, but this worked.

---

### Post by Legace on 2009-05-19
> **Don1500 said:**
> Thanks to Legace!!!

Glad it worked. Enjoy your new usplash ;)

---

### Post by Don1500 on 2009-05-19
I tried with higher resolution but it didn't look as good so I went back to 1024X768.

---

### Post by ilmmpk on 2010-01-03
Mis-Post.  I apologize.

---

