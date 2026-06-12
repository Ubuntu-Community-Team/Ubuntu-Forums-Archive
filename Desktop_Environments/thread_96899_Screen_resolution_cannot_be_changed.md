---
title: "Screen resolution cannot be changed"
date: 2005-11-29
forum: Desktop Environments
---

### Post by dw5437 on 2005-11-29
I have a Gateway 19 inch flat panel monitor and when I go to System-Preferences-screen resolution the only option I have is 640-480. There are no other options. Can I change resolutions or am I going to have to do a new install?
The monitor is recognized on a second computer with Ubuntu 5.10 but not this one.
This is an hp-d325sm with a Amd 939pin 3500 processor.
The other computer that works is an Intel Pentium4
I think I am going to have to reinstall. Any help much appreciated

---

### Post by RAOF on 2005-11-29
No need to reinstall.  You should first try making sure that the X server (the program that actually runs the screen) knows about your other resolutions.  To do this, type the following in a console:
```
sudo dpkg-reconfigure xserver-xorg
```
It will now ask all sorts of questions about your setup.  The default answers should be fine (unless you know they should be different).  At one point, it will ask what resolutions you would like to use.  Here is where you can select what resolutions you want to be available.

---

### Post by handy on 2005-11-29
Yep, I'm new at this too, but I found that you can force higher res' by modifying a config file
probably in /etc/  sorry I've forgotten, but I'll go looking for you.

My Sony 19" is currently running at 1024x768, which is the miminum acceptable these days I think.  I have nVidia 6800GT which I'm preparing myself to install the nVidia drivers for.

I'll get back to you as soon as I find the info' unless someone else gets there first that is :-)

Regards,

handy

---

### Post by handy on 2005-11-29
Look at the service here eh!!

You got a much better answer than I could have given you, while I was still typing mine!!

Beats calling the ms help desk :-)

Cheers,

handy

---

### Post by dw5437 on 2005-11-29
Well I certainly appreciate the answers. I tried the command line option to change resolution and that changed nothing. When I went to change reolution the only choices i had were still the same. Then I decided to restart the computer to see if that might help and now I have a message floating around the monitor that says frequency out of range and it will not boot at all. However I had just received my new cd, so I don't mind reinstalling anyway. I am going to try again after I take a short break. Many thanks for the help!

---

### Post by dcstar on 2005-11-29
[QUOTE=dw5437]Well I certainly appreciate the answers. I tried the command line option to change resolution and that changed nothing. When I went to change reolution the only choices i had were still the same. Then I decided to restart the computer to see if that might help and now I have a message floating around the monitor that says frequency out of range and it will not boot at all. However I had just received my new cd, so I don't mind reinstalling anyway. I am going to try again after I take a short break. Many thanks for the help![/QUOTE]
If you get a monitor frequency message it just means that the PC is trying to send it a signal that it cannot cope with.

Type <CTRL-ALT-F1> and you should get a text login screen, you can then log in as normal and run the previous command to fix up your system without having to to a total re-install.

You can shut down your PC from the command line by (as root user) "init 1", or to reboot "init 6".

---

### Post by RAOF on 2005-11-29
[QUOTE=dcstar]...
You can shut down your PC from the command line by (as root user) "init 1", or to reboot "init 6".[/QUOTE]
Or, even better (you don't need to be root):
To reboot:
```
sudo shutdown -r now
```
To turn off:
```
sudo shutdown -h now
```

---

### Post by aysiu on 2005-11-29
[All the solutions available](http://ubuntuforums.org/showpost.php?p=129379&postcount=21)

---

### Post by skitzot on 2005-11-30
Wow thats complex answers, damn, school me anyday.

I had the same issue with my kds xf-70, what happened is xorg determined my monitor sucked, as in it gave it really, really, crappy refresh rates.  So, I found what the monitor could support, and manually edited, /etc/X11/xorg.conf, after backing it up.

Before:
> 
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection


After:
> 
Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-160
EndSection



Hope this helps!

---

### Post by dw5437 on 2005-11-30
Man, y'all are the best. I didnt try to reinstall yet so I can try your solutions first. I bookmarked all of the pages referred to and will give it a shot. I probably should have searched the forums 1st. My bad

---

