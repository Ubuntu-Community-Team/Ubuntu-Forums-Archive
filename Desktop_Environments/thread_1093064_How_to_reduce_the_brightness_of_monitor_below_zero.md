---
title: "How to reduce the brightness of monitor below zero?"
date: 2009-03-11
forum: Desktop Environments
---

### Post by adit on 2009-03-11
Samsung SynMaster 540N monitor.
I have adjusted the brightness to '0' through buttons provided in the monitor.  I want to reduce the brightness further.  
Is there a way to do it through software settings?

---

### Post by dzark on 2009-03-11
what graphics card are you using?

If it's an nVidia one, and you have their drivers installed, go to System -> Administration -> Nvidia X Settings

In the program, there is a per screen colour correction control which lets you adjust brightness/gamma etc.

---

### Post by adit on 2009-03-11
Graphics card: Intel 915
Driver: vesa-Generic VESA-compliant video cards

---

### Post by oleander on 2009-11-28
I don't have an NVidia graphics card either so I tried this and it was the only way I found to reduce the brightness of the display after already setting the brightness to zero with the display brightness panel applet. Please be careful and use this at your own risk.

First, install "x11-xserver-utils" -- you'll need the "xgamma" program that comes with it.

Open up a terminal and type in:

```
xgamma
```

it should give you the current gamma settings for your monitor -- for example, these were mine:

```
-> Red  1.000, Green  1.000, Blue  1.000
```

Now, if all the settings are the SAME, then you can do this:

```
xgamma -gamma 0.5
```

and that will reduce the gamma of all colours in half -- which will make the monitor appear more dim...

If the current gamma settings are DIFFERENT, then you have to change each colour by hand to make sure that you keep the right ratio. If you want to make a -0.2 change and these are your current settings:

```
-> Red  0.600, Green  0.800, Blue  1.000
```

then you would input this:

```
xgamma -rgamma 0.4 -ggamma 0.6 -bgamma 0.8
```

This method helped me but be careful and use it at your own risk. I'd recommend keeping a brightness applet on your panel (it's available for gnome and you can get the xfapplet program to then use it in xfce as well). I hope this helps.

~oleander

---

### Post by adit on 2009-12-19
> Please be careful and use this at your own riskI will try.  If the risk involves damage to the files, no problem. I can reinstall the operating system.  Is there any risk of damaging the hardware?

---

