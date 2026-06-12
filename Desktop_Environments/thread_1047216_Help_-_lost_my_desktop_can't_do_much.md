---
title: "Help - lost my desktop can't do much"
date: 2009-01-22
forum: Desktop Environments
---

### Post by dougalkerr on 2009-01-22
I am still getting to grips with Ubuntu 8.10 and now I have lost my desktop. After login I get the plain Ubuntu background colour and a terminal window and that's it. I don't know enough about command line workings to get myself out of this so any help is greatly appreciated. Here is the contents of my xorg.conf file (hand typed as I am now in Windows Vista) and the file looks starngely vacant of any kind of drivers. I should have something about my Radeon graphics card I would think...

Section "Device"
        Identifier     "Configured Video Device"
EndSection

Section "Monitor"
        Identifier     "Configured monitor"
EndSection

Section "Screen"
        Identifier     "Default Screen"
        Monitor        "Default Monitor"
        Device         "Configured Video Device"
EndSection

---

### Post by XanTrax on 2009-01-22
> **dougalkerr said:**
> I am still getting to grips with Ubuntu 8.10 and now I have lost my desktop. After login I get the plain Ubuntu background colour and a terminal window and that's it. I don't know enough about command line workings to get myself out of this so any help is greatly appreciated. Here is the contents of my xorg.conf file (hand typed as I am now in Windows Vista) and the file looks starngely vacant of any kind of drivers. I should have something about my Radeon graphics card I would think...

Section "Device"
        Identifier     "Configured Video Device"
EndSection

Section "Monitor"
        Identifier     "Configured monitor"
EndSection

Section "Screen"
        Identifier     "Default Screen"
        Monitor        "Default Monitor"
        Device         "Configured Video Device"
EndSection


You can run 

```

sudo dpkg-reconfigure xserver-xorg

```

That will reconfigure your xorg.conf file and put a default one that works.

Also, have you uninstalled anything lately via command line using remove or purge?

I.E:

sudo apt-get purge <pkg_name>

or

sudo apt-get remove <pkg_name>

Because if so, the package you removed could have removed the ubuntu-desktop package( see: [http://ubuntuforums.org/showthread.php?t=910636](http://ubuntuforums.org/showthread.php?t=910636) )

In that case, do:

```

sudo apt-get install ubuntu-desktop

```

Assuming you're using gnome ubuntu desktop

---

### Post by dougalkerr on 2009-01-23
XanTrax - thanks for the advice and tips but, neither solutions have worked. Looks like I have lost something big time on re-installation. At the moment unfortunately this means using Windows full time till I have free time to try yet another re-install of the operating system. I am sure that there were no errors the last time I installed.
Thanks again...

---

### Post by shark1997 on 2009-01-23
You can try restarting the X server

Code:
startx

---

### Post by XanTrax on 2009-01-23
Alright.  When you get the chance please type

```

sudo su -
lshw -C sound

```

and please post the output of that command.

---

