---
title: "nvidia-settings not staying after reboot"
date: 2015-12-21
forum: Desktop Environments
---

### Post by orazio2 on 2015-12-21
Hello, I have a problem with my computer, an old Compal IFL90 with a GeForce Go 8600GT graphics adapter. As a foreword, I have to say that I extensively researched this problem and still couldn't solve it. I have xubuntu 14.04 installed, and am trying to make the screen settings I choose from nvidia-setting stick between reboots.


I have a Sharp LCD television that I want to use as an external monitor, with the laptop screen off. I couldn't set its resolution to 1920x1080, as nvidia-settings only allowed the resolution options shown in the figure below.
[IMG]http://s22.postimg.org/5xcg8nvkh/Screenshot_21122015_10_15_12.png[/IMG]

 I solved the problem by installing nvidia-340 from the ubuntu repositories. After that (and only with the 340 version, no other one will do), I can set the resolution I want with the advanced options from nvidia-settings, also shown, in the other image. 
[IMG]http://s22.postimg.org/bzk2z5k0h/Screenshot_21122015_10_16_43.png[/IMG]
Problem is, it doesn't stick after reboot. I get the wrong resolution on the sharp lcd, and the laptop monitor on each time I turn on the computer.


I've tried everything that can be found searching on the internet about this topic. Some highlights. Saving to xorg.conf doesn't work, and the xorg.conf file produced by nvidia-settings doesn't contain any info about resolution. Therefore, "nvidia-settings --load-config-only" doesn't work as well. I tried creating a config file with "sudo nvidia-xconfig" but it looks like the same file as the one produced witn nvidia-settings. I can't set things with an external script on startup, as xrandr doesn't work when I try to allow different rersolutions or change the resolution via command line. There is no monitors.xml in my ~/.config/ folder.


I'm a bit confused here. Have you got any suggestions? Whatever other info is needed just ask, and I'll post it.


Thanks in advance.


p.s. as a sideline, I can't even make the command "xset s off" stay between reboots. I tried putting it in the ~/.xinitrc (which was empty) and in /etc/X11/xinit/xinitrc (which already existed), but none works. I suspect therefore that none of the two scripts is being executed at X startup.

EDIT:
some additional info that might be useful: I am using a VGA cable, which works perfectly well with 1920x1080 resolution,  and the computer is so old that it hasn't got HDMI.

---

### Post by grahammechanical on 2015-12-21
What cable are you using to connect to the monitor? VGA or DVI or HDMI?

I have a desktop not a laptop. So, I am not in the exact same situation as you. But I am using a Sharp TV as a monitor and it is being run at 1920x1080 resolution both with the open source video driver and the Nvidia 340 proprietary video driver.

When I first brought this Sharp TV I did not have an HDMI cable to use for the connection. So, I used a VGA cable and the maximum resolution available was much reduced from what the screen was capable of. Using an HDMI cable fixed this particular problem for me.

Regards.

---

### Post by orazio2 on 2015-12-22
I am using a VGA cable, and cannot use the HDMI, as there is no such connector on the computer (it was bought in 2007).
Nonetheless, I probably wasn't clear in the explanation of the problem. I am perfectly able to use the monitor on 1920x1080. My problem is that, whenever I reboot, the resolution  settings are lost, and I don't know how to make them stick.

---

