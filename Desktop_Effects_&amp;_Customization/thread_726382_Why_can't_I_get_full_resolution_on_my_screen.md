---
title: "Why can't I get full resolution on my screen?"
date: 2008-03-16
forum: Desktop Effects &amp; Customization
---

### Post by TattooedRunes on 2008-03-16
Here's my stats:

Running Gutsy on an HP with a 17' 1440X900 
Card is GeForce Go 7600
Drivers are in and running fine.  Desktop effects and screen savers run and look great.

Here's the issue:
I can't get anything more than 1024X786 out of the "Screens and Graphics" tool.
I'd like to be able to view the way my monitor should viewed

Help!

---

### Post by FuturePilot on 2008-03-16
Don't use the Screen and Graphics tool with the Nvidia driver. Use the Nvidia Settings instead.
```
gksudo nvidia-settings
```
Click on X Server Display Settings. Make sure you Save to X Configuration File so the settings stay.

---

### Post by Kabezon on 2008-03-17
If you still have problems try using [Envy]("http://www.albertomilone.com/nvidia_scripts1.html")[1] and letting it automatically configure X.

[1]"[Envy]("http://www.albertomilone.com/nvidia_scripts1.html")" is an application for Ubuntu Linux and Debian written in Python and PyGTK which will:
1) detect the model of your graphic card (only ATI and Nvidia cards are supported) and install the appropriate driver. However automatic detection can be overridden with the "Manual installation"
2) package the driver that comes with ATI or Nvidia's installer (from their respective websites)
3) install all you need to package and install the driver
4) configure the Xserver for you

Envy features both a GUI (which you can launch only inside a Desktop Environment) and a textual interface which you can use if, for example, you cannot start the Xserver.

---

### Post by TattooedRunes on 2008-03-21
Hey I tried both of your suggestions and just as before... no luck.  

The NVIDIA settings tell me this:

Native Resolution: 1440*900
Best Fit Resolution: 1440*900

Frontend Resolution: 1024*786                <===== The Problem!!!
Backend Resolution: 1440*900

in the X Server Display Configuration, it doesn't give me an option for 1440*900, and "auto" gives me rotten old 1024*786.

---

