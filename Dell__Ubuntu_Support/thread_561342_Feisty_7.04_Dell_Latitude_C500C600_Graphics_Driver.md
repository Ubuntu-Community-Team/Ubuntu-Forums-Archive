---
title: "Feisty 7.04 Dell Latitude C500/C600 Graphics Drivers"
date: 2007-09-27
forum: Dell  Ubuntu Support
---

### Post by perrinoia on 2007-09-27
I am an Ubuntu novice who has just installed Ubuntu Feisty 7.04 on my old Dell Lattitude C500/C600 and have 3 issues.

[LIST=1]
[*]Maximum screen resolution is 800x600, while the LCD panel is capable of up to 1024x768.

I downloaded 4 different ATI drivers from dell.com that are Linux compatible. But they are in RPM format, and Ubuntu claims to not recognize this format. A friend mentioned something about compiling a kernel with them, but I don't know what that means.

I read another thread where someone posted the following instructions for Lattitude users with high resolution displays, but I'm not sure if this applies to me as my display is only 1024x768.
> Secondly, if you have one of the wonderful high resolution displays (1400×1080), it won’t work correctly. It’s pretty easy to fix.

    * Boot into the horrible looking wrong resolution
    * Crack open a terminal
    * Type “sudo gedit /etc/X11/xorg.conf”

Add the Sync / Refresh lines into the Monitor section so it looks like this:

Section "Monitor"
Identifier "Generic Monitor"
Option "DPMS"
HorizSync 28-70
VertRefresh 43-60
EndSection

Then add the full resolution into each of the modes, so they all look like this:

SubSection "Display"
Depth 24
Modes "1400x1050" "1280x1024" "1024x768" "800x600" "640x480"
EndSubSection

That’s it - now save and reboot, and you should be working in full resolution. Hurrah!

[*]My Belkin 802.11G PC card doesn't work with it. Ubuntu recognizes that there is a Belkin PC card connected, but doesn't do anything with it.

I was unable to find any Linux compatible drivers for this device.


[*]When I installed Ubuntu, it added a nifty little scrolling feature to my 6 year old touch pad that never scrolled with windows before. But that feature has since disappeared. How do I get it back?

The only change I recall making since I last used the touch pad scroll feature was plugging in an optical mouse with scroll wheel. I have since unplugged the mouse and the scroll feature did not return.
[/LIST]

---

### Post by dandanplan on 2007-09-27
Hi,

1.
I don't know which ATI Card is in your Laptop would be nice if you could tell. But anyway you have two options a. radeon or b. fglrx.

Check here: [http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

In short for the terminal: 
$ sudo aptitude install linux-resticted-modules-generic #for fglrx
$ lsmod | grep fglrx # look if the fglrx module is running
$ lsmod | grep radeon # or for the radeon module
$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup #Backup the file in case...
$ sudo dpkg-reconfigure xserver-xorg

Hint: if you are unsure what you should choose leave it the way it is. When you are asked for the Driver choose radeon or fglrx. At the end of the dialogs you are asked for the resolution choose the ones your system can handle. Choose at monitor-layout simple. 

2. With the Belkin I can't help, maybe search the Ubuntu Hardware Database.

3. For the touchpad:
$ sudo gedit /etc/X11/xorg.conf 

Search for Section "InputDevice", there will be more than one. Look if you can find one like this (if not add this to your file):

```
Section "InputDevice"
    Identifier     "Synaptics Touchpad"
    Driver         "synaptics"
    Option         "SendCoreEvents" "true"
    Option         "Device" "/dev/psaux"
    Option         "Protocol" "auto-dev"
    Option         "HorizScrollDelta" "0"
EndSection
```

See the Option "HorizScrollDelta" "0"? This gives you the scrollability for your touchpad.
Save the file. And close gedit.

Now you can restart your system
$ sudo shutdown -r now #restart your system

If anything went wrong, and you have no graphical system at all:
login in the Terminal Ctrl+Alt+F1

$ sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf

Replace your edited file with your backuped one.
And restart
$ sudo shutdown -r now

I hope I could help.
dandanplan

---

