---
title: "need help with loading GUI"
date: 2005-12-21
forum: Desktop Environments
---

### Post by emerick7 on 2005-12-21
I followed through the instruction on [transparent terminals on the ]("https://wiki.ubuntu.com/TransparentTerminals?highlight=%28transparent%29%7C%28terminals%29")wiki, and then when I got to the part to restart x with control-alt-backspace, everything when black and I got a command prompt-type screen. I tried restarting it, and when it's finished going through the OKs (nothing errors out) during startup, I get a screen that says 
> Failed to start the X server (your graphical user interface).  

I'm not able to get anywhere. After that, it just goes into a command prompt again where it asks for login info, but I don't know where to go from there. How do I go to a safe mode or something similar so I can revert back to what I had before? At this point, I don't want transparent terminals anymore - I just need to get my desktop running.

I'd appreciate the help... I really need some this time. Thanks!

edit - I first posted this in response to a thread in the Customization Tips and Tricks section.  I didn't realize questions were not allowed there until after I posted it... sorry.

Also, I tried the command 'startx,' and it went through some lines and didn't load anything.  I saw that it had some problems with the lines I added according to the wiki instructions.> 5. Modify your xorg.conf file to enable compositing. Add the following lines after the "Modules" section in /etc/X11/xorg.conf 

 Section "Extensions" 
 Option "Composite" "Enable" 
 EndSection

Add the following to the "Device" section 

 Option "RenderAccel" "true" 
 Option "AllowGLXWithComposite" "true"


I then realized that I added the lines "section extensions" and "option composite enable" in the modules section, not after.  This might be the problem, but I don't know how to get in to fix it.

---

### Post by dcstar on 2005-12-21
[QUOTE=emerick7].......I don't want transparent terminals anymore - I just need to get my desktop running.
......[/QUOTE]
Open a terminal:

sudo dpkg-reconfigure xserver-xorg

This will create a new xorg.conf file, save the existing one if you really want it.

---

