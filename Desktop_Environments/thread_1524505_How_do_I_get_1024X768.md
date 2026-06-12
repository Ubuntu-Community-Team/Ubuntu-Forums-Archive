---
title: "How do I get 1024X768?"
date: 2010-07-05
forum: Desktop Environments
---

### Post by Philip dT on 2010-07-05
Hallo. I am new here.
 
I have successfully downloaded and installed the latest ubuntu, and I am trying to get 1024X768 screen resolution.
 
Hardware: K8M800 VIA Onboard video (I only get 800X600).
 
I am trying to edit my xorg.conf file.
 
When I open a terminal window, and put in:
 
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
 
It says that it does not see such a file. Do I need to change the directory? If so, how do I do it.
 
Also, if I put in this in the terminal window:
gksudo gedit /etc/X11/xorg.conf 
then the file is blank, and if I want to save, it says that such a file does not exit.
 
What am I doing wrong?
 
(Remember I am completely new to ubuntu)

---

### Post by Frogs Hair on 2010-07-05
Have you tried system> preferences> monitors and set the resolution from the GUI.

---

### Post by hictio on 2010-07-05
The modern X Window doesn't use the '/etc/X11/xorg.conf' file, or, if it does, the configuration is dynamic.
Try setting things up using the GUI tool (like Frogs Hair suggested), and see if it helps?

---

### Post by Philip dT on 2010-07-06
Hallo. I tried changing the resolution via system> preferences> monitors, but it only gives me 800X600. It says the monitor is unknown. I tried to "detect monitor" but that does not work either.
 
This is a Proline 17" Crystalview 7VlR CRT monitor that can do 1280X1024 (60KHz), but the resolution I want to use is 1024X768 (85KHz).

---

### Post by cutekazuya on 2010-07-06
hi mate,

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak

does not work because you are trying to copy a file that does not exist

Try this:

```
sudo gedit /etc/X11/xorg.conf 
```

copy the following in your xorg.conf: 

```
Section "Monitor" 
    Identifier     "Monitor0" 
    VendorName     "Unknown" 
    ModelName      "Proline 17 Crystalview 7VlR" 
    HorizSync       30.0 - 70 
    VertRefresh     50.0 - 85 
EndSection 
 
Section "Device" 
    Identifier     "Device0" 
EndSection 
 
Section "Screen" 
    Identifier     "Screen0" 
    Device         "Device0" 
    Monitor        "Monitor0" 
    #DefaultDepth    24 
    SubSection     "Display" 
        #Depth       24 
        Modes     "1024x768" "800x600" "640x480" 
    EndSubSection 
EndSection
```

Your login screen will be 1024x768 and once you login, you can set your user screen resolution under system> preferences> monitors to whatever you like.

If this dont work, try changing the HorizSync and VertRefresh rates to match your monitors.

---

### Post by Philip dT on 2010-07-14
Hallo cutekazuya.
 
Thanks for your reply.
 
I managed to create a new file called "xorg.conf" and saved it in the root.  But that does not seem to work.  Where must the file be saved?

---

### Post by Philip dT on 2010-07-14
O wait, it worked.  Of course, in the etc/X11 directory.  Thanks, you're a star

---

