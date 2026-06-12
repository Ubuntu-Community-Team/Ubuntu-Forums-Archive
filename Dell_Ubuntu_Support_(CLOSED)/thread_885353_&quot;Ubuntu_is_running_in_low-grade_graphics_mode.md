---
title: "&quot;Ubuntu is running in low-grade graphics mode&quot;"
date: 2008-08-10
forum: Dell Ubuntu Support (CLOSED)
---

### Post by TimDaniels on 2008-08-10
I just upgraded from a working Gutsy to a problematic Hardy on my XPS-M1330 laptop with the Nvidia graphics card.  At startup, a message box comes up that says "Ubuntu is running in low-grade graphics mode".  The graphics that eventually comes up if I say to continue is low-resolution (larger icons and fonts).  Checking System/Administration/Hardware Drivers shows that the latest Nvidia driver is installed (or so it says), but the entry that used to list firmware is missing.  Has anyone any idea what is wrong?  The laptop was working fine under Ubuntu 7.10.

*TimDaniels*

---

### Post by TenPlus1 on 2008-08-10
Pop into Screens and Graphics in the Applications -> Other menu and select your monitor from the list (or closets) so you can use hi-res screen selection...  This is what I had to do so i could get my 1280x1024 LCD monitor working on a bigger res than 640x480...

---

### Post by cdtech on 2008-08-10
Have you tried:
```
sudo nvidia-settings
```

---

### Post by TimDaniels on 2008-08-10
> **TenPlus1 said:**
> Pop into Screens and Graphics in the Applications -> Other menu and select your monitor from the list (or closets) so you can use hi-res screen selection...

    I searched through all the apps listed in "All" and "Other" and "Graphics" in Applications/Add_Remove, but there was nothing in the way of Screens and Graphics.  And System/Preferences/Screen Resolution had 800x600 as the highest resolution available.

*TimDaniels*

---

### Post by TimDaniels on 2008-08-10
> **cdtech said:**
> Have you tried:
```
sudo nvidia-settings
```

I got "command not found".

*TimDaniels*

---

### Post by cdtech on 2008-08-10
If "sudo nvidia-settings" dosen't work for you, you could try and reset the xorg.conf file by booting into recovery mode, log in and type "sudo dpkg-reconfigure xserver-xorg" then reboot.

Hope this helps...

**P.S.**
> I got "command not found".
That just means its not installed.

---

### Post by TimDaniels on 2008-08-10
> **cdtech said:**
> If "sudo nvidia-settings" dosen't work for you, you could try and reset the xorg.conf file by booting into recovery mode, log in and type "sudo dpkg-reconfigure xserver-xorg" then reboot.

Hope this helps...

**P.S.**

That just means its not installed.

Before your reply, I tried comparing the xorg.conf file with the one I used for Gutsy, and they were slightly different in the "screen" section, so I commented out the extra options.  But the same error box appeared announcing "... low-grade graphics mode" after startup.  I then realized that the error box itself allowed settings to be made - selection of a driver according to graphics card manufacturer and graphics card line.  So I fiddled with that, picking Nvidia's 8 Series and 1280x1024 resolution and 60Hz refresh rate, and the error box at startup (and the repeated 3 presentations of 5 command lines) no longer appeared.  Further fiddling with System/Preferences/Appearance got the font and icon sizes down to a suitable size.  The screen resolution problems seem to have been solved, at least for now, and now I can move on to figuring out why the xorg.conf file's screen section is now so complex.  :)  Thanks for your encouragement!

*TimDaniels*

---

### Post by TenPlus1 on 2008-08-10
Screens and Graphics is hidden by default (go figure), so to get it to appear, right-click on the menu, Edit Menu's and look for OTHER, then tick the box next to Screens and Graphics for it to show...

---

