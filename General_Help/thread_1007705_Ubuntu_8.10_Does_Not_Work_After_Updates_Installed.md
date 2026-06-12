---
title: "Ubuntu 8.10 Does Not Work After Updates Installed"
date: 2008-12-10
forum: General Help
---

### Post by tallnerd1985 on 2008-12-10
Hello everyone, I am a little new to the Ubuntu Linux scene so here it goes.  I had WinXP installed and then I installed Ubuntu 8.10 on a seperate partition.  Everything worked fine, I could boot either in Windows or Ubuntu without any kinda of problems.  While playing around in Ubuntu, I enabled the Nvidia 173 drivers so that I could use the compiz features and I also had the update manager go thru and update Ubuntu.  It prompted me to restart the computer and when I try to select the new Kernel to boot, it makes it thru the splash screen but when it normally gets to the GUI login screen, it boots into a terminal interface screen where it asks me to login.  I type my username and password but after that, nothing else happens besides showing me that I am logged into a certain directory.  How do I get the GUI back on?

---

### Post by taurus on 2008-12-10
Sounds like you need to reconfigure your X server again.  Try running these commands from the prompt and see what happens.

```
sudo dpkg-reconfigure -phigh xserver-xorg
startx
```

---

### Post by element_G on 2008-12-10
This is a more manual way to do things than what taurus posted (which should work anyway) So disregard most of my post if you already have a working X server 

The reason why you are sent to a console login is because X cannot be started (the GUI), this is most likely due to a problem with the nvidia driver. 

To get a working X again you will need to tell it to use the ' vesa ' driver instead of ' nvidia ' 
Start at the console login

0. type ```
sudo /etc/init.d/gdm stop
``` if it says gdm is not started don't worry, just continue 

1. Make a backup of your xorg.conf (this is the file that tells your PC what to do with your display)
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```2. Edit your xorg.conf
```
sudo nano /etc/X11/xorg.conf
```Scroll down to the lines that look like this
```
Section "Device"
    Identifier    "name of your graphics card"
    Driver        "nvidia"
    BusID        "PCI:0:2:0"
EndSection
```And change "nvidia" to "vesa"
Save the changes by pressing Ctrl+X (to exit) and then y (to save changes)

now you can see if X will start with 
```
sudo /etc/init.d/gdm start
```This will get you back into X but you won't be using nvidia, to get things re-enable install envy-ng (once installed, run it with sudo envyng-gtk)
```
sudo apt-get install envyng-gtk
```

---

### Post by element_G on 2008-12-10
sorry, double post

---

### Post by tallnerd1985 on 2008-12-10
I tried the first method but go this error:

Primary device is not PCI
(EE) No Device detected

[B]Fatal server error:
No Screens Found
giving up.
xinit: connection refused (errno 111): unable to connect to x server
xinit: no such process (errno 3): server error.[/B]

I will try the other method here in a sec

---

### Post by tallnerd1985 on 2008-12-10
I tried your method element_G but when I was editing the /etc/X11/xorg.conf file, I noticed that it had writing in it but it kinda looked liked no settings were placed.  It look like all the fill in the "display device" and such were all generic.  Is there anything else I could do?

---

### Post by taurus on 2008-12-10
Can you post your /etc/X11/xorg.conf?

```
cat /etc/X11/xorg.conf
```

---

### Post by element_G on 2008-12-10
what is the output of ```
lspci | grep VGA
```

---

### Post by tallnerd1985 on 2008-12-10
Here is what it says when I open it up

[B]Section "Device"
       Indentifier         "configured video device"
EndSection

Section "Monitor"
       Indentifier         "configured Monitor"
EndSection

Section "Screen"
       Identifier          "Default Screen"
       Monitor             "Configured Monitor"
       Device              "Graphics Device"
Endsection[/B]

---

### Post by taurus on 2008-12-10
Try booting into recovery mode from GRUB menu and pick the fix Xserver option to see if that fixes the problem.

---

