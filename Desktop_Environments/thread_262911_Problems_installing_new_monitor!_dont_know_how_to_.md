---
title: "Problems installing new monitor! dont know how to install driver etc.."
date: 2006-09-22
forum: Desktop Environments
---

### Post by bubi1980 on 2006-09-22
Hi,

I have a new monitor (Samsung SyncMaster 203B 20"), i just bought it yesterday and dont know how to install the driver for it. In the documentation of the monitor I can find something about how to install it under Linux (X-Windows and X86Config file...) but I dont how to do it.
When I start the computer with the new monitor it tells me (after loading ubuntu but before loging in) that "screen resolution is not optimal", and I have to change it to 1400*1050 at 60Hz. But in the preferences-->screen resolution, there is no 1400*1050!
Can someone help me out with this please?

ps: the monitor is working fine on 800*600 but if I change it, the screen gets messed up with black squares and lines etc...
Edit/Delete Message

---

### Post by _simon_ on 2006-09-22
You don't need a driver.

Try this:

In terminal

```

sudo gedit /etc/X11/xorg.conf

```

Scroll down to 
```

Section "Screen"

```

You will see a list of screen resolutions like this:

```

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40 [GeForce 6800]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

In the MODES line, at the start add "1400x1050"

like this:

```

Modes      "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"

```

Save the file.
Log out
Press CTRL ALT BACKSPACE
Log back in

See if it now gives you the correct resolution.

If not then it may be because you need to change video drivers e.g. you may have an nvidia card and be using "nv" rather than "nvidia" - your xorg will confirm which you are using in the Device section. - let us know what you are currently using.

Hope this is of some help... any problems then let us know what is or isn't happening.

---

### Post by bubi1980 on 2006-09-22
it works !!

thank you :D

---

### Post by _simon_ on 2006-09-23
Good good :)

---

### Post by denis125 on 2006-11-01
You don't need a driver.

Try this:

In terminal


Code:
sudo gedit /etc/X11/xorg.conf

I have the same problem I'not bilingual where in terminal
What do you means by in terminal

Thank you

---

### Post by SirPecanGum on 2006-11-12
Worked for me on my new monitor too. Thanks!

---

### Post by Matthijs on 2007-01-28
Hello there, 

its seems that configuring the samsung 203B 20" is not a big problem at a resolution of 1400 x 1050. But my monitor doesn't seems to position right. If i set my samsung 203b to a resolution of 1400 x 1050, the screen is position to the right and down. So i got a black border to the left. I've followed a lot of forums and books to solve my problem... I find it odd that you all have no problem at all when reconfigering the xorf.conf file. 

I found someone with the same problem [here]("http://ubuntuforums.org/showthread.php?t=300109&highlight=203b")

Any thought anyone?

Matthijs

---

### Post by Matthijs on 2007-01-28
I've made a picture with my camera to show you my problem. you see that the screen is position to the right and slight down (normally you would see the task bar)

---

### Post by vehlewa1 on 2007-02-07
I am having a similar problem, except mine is happening during the installation.  I have a Radeon 9550 card, on an AMD64 processor, using a 19 in Samsung Syncmaster monitor.  I boot with the Ubuntu installation disk, and after the installation fully loads into memory (about 3 minutes in), my monitor flashes and says 'Not Optimal' then gives a recommended resolution and hrz level.  The screen goes black (still powered on, but broadcasting a black signal) and nothing else loads.

It appears that as soon as the graphical interface for the installer tries to load, this happens and best I can tell the computer stops working all together.  I've allowed the machine to sit for hours on one occasion to see if the installation continues or if any other activity happens at all but it does not.  

I am relatively new to Linux (Used Suse 10.1 for a short period, but wanted to get Ubuntu running), but is there any other solution that I can try?

I've tried to install using Kubuntu which allows me to install the operating system, but as soon as I reboot I get the same message as above.  

Thanks So Much.

-M

---

### Post by ekureuil on 2007-04-30
Hi ! 
I already got this problem of screen going to the right,autoconfiguration doing wrong things and manual configuration being not sufficient... after some search, it revealed to be (at least for me) a modeline problem.

This code worked for me:
```

Section "Monitor"
        Identifier      "SyncMaster"
        Option          "DPMS"
        HorizSync       28-49
        VertRefresh     43-72
        Modeline "1400x1050" 123.91  1400 1464 1616 1896  1050 1050 1052 1089
EndSection

```

Hope this helps !

Bye.

---

### Post by sunkssss on 2007-12-03
> **_simon_ said:**
> You don't need a driver.

Try this:

In terminal

```

sudo gedit /etc/X11/xorg.conf

```

Scroll down to 
```

Section "Screen"

```

You will see a list of screen resolutions like this:

```

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40 [GeForce 6800]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

In the MODES line, at the start add "1400x1050"

like this:

```

Modes      "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"

```

Save the file.
Log out
Press CTRL ALT BACKSPACE
Log back in

See if it now gives you the correct resolution.

If not then it may be because you need to change video drivers e.g. you may have an nvidia card and be using "nv" rather than "nvidia" - your xorg will confirm which you are using in the Device section. - let us know what you are currently using.

Hope this is of some help... any problems then let us know what is or isn't happening.

I'm having a similar problem, but when i enter sudo gedit /etx/x11.conf into terminal the window that pops open is empty. Why is this happening? I have an ATI Radeon 7500 running Gutsy.

---

### Post by sunkssss on 2007-12-03
> **_simon_ said:**
> You don't need a driver.

Try this:

In terminal

```

sudo gedit /etc/X11/xorg.conf

```

Scroll down to 
```

Section "Screen"

```

You will see a list of screen resolutions like this:

```

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV40 [GeForce 6800]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

```

In the MODES line, at the start add "1400x1050"

like this:

```

Modes      "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"

```

Save the file.
Log out
Press CTRL ALT BACKSPACE
Log back in

See if it now gives you the correct resolution.

If not then it may be because you need to change video drivers e.g. you may have an nvidia card and be using "nv" rather than "nvidia" - your xorg will confirm which you are using in the Device section. - let us know what you are currently using.

Hope this is of some help... any problems then let us know what is or isn't happening.

I'm having a similar problem, but when i enter sudo gedit /etx/x11.conf into terminal the window that pops open is empty. Why is this happening? I have an ATI Radeon 7500 running Gutsy.

---

