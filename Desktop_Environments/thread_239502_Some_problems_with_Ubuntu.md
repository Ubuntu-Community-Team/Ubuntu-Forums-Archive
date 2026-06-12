---
title: "Some problems with Ubuntu"
date: 2006-08-19
forum: Desktop Environments
---

### Post by vnt87 on 2006-08-19
Hello all,
I'm pretty new not just to Ubuntu, but to Linux in general, so if my questions seem to be obvious, please pardon me. I just dropped Windows a few days ago and installed Ubuntu from a CD sent to me thru ShipIt, and I love it, but I have some problems with it though.

1. My screen resolution is locked in at 1280x1024@60Hz by default, I cant change it no matter what. f I go to System>Preferences>Screen Resolution and change to any other resolutions, it boots me to the login screen and I had to login again.
I searched this forum and found some other ways to change resolution but none of them worked. I tried using the 915resolution tool to force resolution change, but if I do that, it gives me a blank screen after reboot.
I also tried the 'dpgk-reconfigure xserver-xorg' that was mentioned in other thread, but it also gave me a blank screen after restarting X.
So what's the problem here? My graphic card is an integrated Intel using the i810 driver if that mean anything?

2. After a few days of using, the Synaptic Packgage Manager and everything associated with it are not working anymore. When I launch it, I see only the dialog that prompts for root password, after I entered the password, nothing happen, it does not open. Samething happen with the Add/Remove tool, at least I can still see the package list in it, but can't actually add or remove anything.

Can anybody help me with these?

---

### Post by foolsh on 2006-08-19
1. What resolution and refresh rate are you shooting for?

2. Its likely not a problem with your video card asmuch as it is with your monitor

C. Are you sure you monitor can display wanted resolution + refresh rate?

#FF00. "sudo dpgk-reconfigure synaptic" might help but most likely won't

---

### Post by vnt87 on 2006-08-19
I'm trying to set it to 1024x768@75Hz (or 70Hz, doesn't matter). I also thought it might be something wrong with my monitor. But back when I was using Windows, it was fine at 1024x768 even at 80Hz.

Btw, that command for Synaptic doesn't do anything :(

---

### Post by foolsh on 2006-08-19
have you tried "sudo synaptic"

try "sudo gedit /etc/X11/xorg.conf"
and change your monitor section to something like this omitting the <--comments

```
Section "Monitor"
        Identifier      "left"        <----DON'T CHANGE THIS ON YOURS
        Option          "DPMS"
        HorizSync 30-100              <---------add these lines
        VertRefresh 75                <---------
EndSection

```
and scroll down to the screen section and make it resemble this

```
Section "Screen"
        Identifier      "leftscreen" <--------DON'T EVEN THINK ABOUT CHANGING IT
        Device          "intel"    <----THIS ONE EITHER    
        Monitor         "left"   <-----NOPE NOT THIS LINE
        DefaultDepth    24
        SubSection "Display"
                Depth           24   
                Modes           "1024x768" <-------here you are change this if there was other stuff here you can delete it if you only want this resolution
        EndSubSection
EndSection
```

---

### Post by vnt87 on 2006-08-19
Thanks for your input, when i entered sudo synaptic, it displays some errors about libvte. Apparently this was caused after I updated compiz. Good thing this problem has been addressed and made a sticky in this forum.

But I couldn't do anything with the resolution, I tried editing the xorg.conf like you said and it displays a black screen after I reboot or restart X.

Is there any other ways to fix the res.

Thanks for your help.

---

### Post by foolsh on 2006-08-20
could you post your xorg.conf file here and let me hava look see?

---

