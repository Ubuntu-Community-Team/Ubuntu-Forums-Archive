---
title: "no desktop"
date: 2006-04-18
forum: Desktop Environments
---

### Post by re-entity on 2006-04-18
I'm running Ubuntu, Breezy Badger. Half way through booting I loose my GUI and end up with an unhelpful message about an X server (crashed/corrupted) and then a message that says GDM is disabled.

I can then log in as usual (without a GUI) and have access to the terminal.

How do I go about repairing Gnome? I am a total Linux noob so baby steps please.

I have access to both an install and live Ubuntu cd. Is there some repair feature either on the CDs or through the terminal?

---

### Post by Sutekh on 2006-04-18
Have you only just installed Ubuntu?  What sort of video hardware do you have?

Issue this command to setup the X Windows Server from the command line```
sudo dpkg-reconfigure xserver-xorg
```
You will be asked a long string of questions regarding your input devices; mouse/keyboard/monitor.

If you are unsure what to answer, just accept the default/suggested values.

If you have issues with the video driver, you should probably choose the **vesa** driver for now to get things working

When that is finished use
```
sudo /etc/init.d/gdm restart
```to get the GUI going again.

---

### Post by re-entity on 2006-04-18
Ubuntu was working fine until recently. It isn't a new install.

I have an ATI Radeon 9600XT graphic card.

---

### Post by re-entity on 2006-04-18
Thanks Sutekh. That worked perfectly! Using Ubuntu again :)

---

### Post by Sutekh on 2006-04-18
Cool, nice work.

You may want to check out installing ATI specific drivers, as the vesa driver is a kind of one fits all solution.

These are some links I know of for ATI cards

[Ubuntu Wiki - Binary Driver HOWTO](https://wiki.ubuntu.com/BinaryDriverHowto)

[Unofficial ATI Linux Driver Wiki](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide)

or look into installing EasyUbuntu (for GUI install of ATI drivers and loads of other stuff)

[Ubuntu Forums - Easy Ubuntu v2.2](http://ubuntuforums.org/showthread.php?t=64629)

---

