---
title: "No graphical login after new vid card install"
date: 2006-01-05
forum: General Help
---

### Post by shewbox on 2006-01-05
I switched out my newer ATI card for an older NVIDIA card (driver issues), but after getting the newest NVIDIA drivers working, Ubuntu now boots into a text terminal instead of the graphical login.  How does one go about getting the graphical login to start up at boot time?

---

### Post by professor_chaos on 2006-01-05
to start, if you want graphical login you can change the driver from nvidia to nv by...
```
sudo vi /etc/X11/xorg
```
edit the line in the section 
```
Section "Device"
        Identifier      "NVIDIA Corporation NV36 [GeForce FX 5700 VE]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
EndSection
```
to
```
Section "Device"
        Identifier      "NVIDIA Corporation NV36 [GeForce FX 5700 VE]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection
```

Then you should install all of the nvidia drivers from synaptic. After this you should configure your xserver by
```
sudo dpkg-reconfigure xserver-xorg
```

Check this thread out. And if you type nvidia in the search bar in this forum you will find quite a few threads on this issue.
[http://www.ubuntuforums.org/showthread.php?t=75074&highlight=reconfigure+xserver](http://www.ubuntuforums.org/showthread.php?t=75074&highlight=reconfigure+xserver)

---

### Post by Aphorism on 2006-01-05
You have crankied your xwindows configuration.

Simply try this

```
sudo nano /etc/X11/xorg.conf
```

And scroll down to your video card device.  Change the "Driver" line from "nvidia" to "vesa" and then start sorting out why your Nvidia drivers aren't working.

---

### Post by shewbox on 2006-01-06
I really appreciate your help, however I messed up and didn't give enough information in my original post to correctly solve the problem.  

When I first boot up, I see only a text login, but if I login and type 'startx' gnome boots up just fine and everything is peachy.  If I try to log out of gnome, the only option I have is to 'Log Out', and it takes me back to the terminal, not the graphical login screen.  I can type 'sudo gdm' and then the graphical login will start up and function normally, which gives me more options when I try to logout such as 'Shut Down', 'Restart the Computer', 'Hibernate'.  Logging out takes me back to the graphical login screen, instead of the terminal.  

So, I suppose I should rephrase the question to:  how to I get gdm to start at boot time, and why did it stop loading at bootup when I installed new vid card and drivers?

---

### Post by handy on 2006-01-06
Which model nVidia card?

I have a suspicion that the new drivers don't cover the older cards.

The nVidia site will have this info' if it is relevant.

handy

---

### Post by shewbox on 2006-01-06
It is an Nvidia Geforce FX 5200, which is a supported card in the newest drivers according to this page:  [http://www.nvidia.com/object/IO_18897.html]("http://www.nvidia.com/object/IO_18897.html")

---

### Post by handy on 2006-01-08
[QUOTE=Aphorism]You have crankied your xwindows configuration.

Simply try this

```
sudo nano /etc/X11/xorg.conf
```

And scroll down to your video card device.  Change the "Driver" line from "nvidia" to "vesa" and then start sorting out why your Nvidia drivers aren't working.[/QUOTE]


Shewbox, did you follow the above advice?

It may solve the problem...

handy

---

### Post by dcstar on 2006-01-08
[QUOTE=shewbox]
.....
So, I suppose I should rephrase the question to:  how to I get gdm to start at boot time, and why did it stop loading at bootup when I installed new vid card and drivers?[/QUOTE]
In /etc/rc2.d there should be a file called "S13gdm", if it is there, then when you boot up without the graphical login, type in a terminal:

sudo /etc/init.d/gdm start"

and see if any messages appear to let you know what has happened.

---

### Post by slux on 2006-01-08
I don't know what would cause gdm to be removed from the runlevel but an "update-rc.d gdm defaults" will pretty much sort it out if you happen to be missing the symlink pointed out in the previous post.

---

### Post by shewbox on 2006-01-08
Looking in /etc/rc2.d I see the file called "S13gdm".  However, typing 'sudo /etc/init.d/gdm start' gives this message:

```
[sudo: /etc/init.d/gdm: command not found 
```

And, consequently, I also get the same message when trying 'update-rc.d gdm defaults'

```
ben@ubuntu:/etc/rc2.d$ update-rc.d gdm defaults
update-rc.d: /etc/init.d/gdm: file does not exist

```

Also, I'm getting a bit confused.  I can type 'sudo gdm' and that will get it running.  Is there a location where the command 'gdm' actually exists and a symlink for that command usually lies in /etc/init.d and that is what is missing on my system for it to run on boot time?  Is 'gdm' a program that usually runs at startup, or is it some sort of graphical server related to xorg or am I just way off base here?

---

### Post by az on 2006-01-08
Actually, it's 

sudo /etc/init.d/gdm restart

and to reconfigure x (including autodetection (just changing the driver is not enough - you may need to alter the pci address)

sudo dpkg-reconfigure xserver-xorg

Then 
sudo nvidia-glx-config enable
(assuming you have all the nvidia-glx packages installed along with the restricted modules)

Also, try

sudo apt-get install --reinstall gdm

 if everything else fails.

---

