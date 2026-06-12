---
title: "Beryl Problem"
date: 2007-01-04
forum: Desktop Environments
---

### Post by Nvening on 2007-01-04
I have just installed Beryl but i get this error message when i try to run it. What does it mean?

I have an ATI x800xt with the ATI drivers installed.

```
XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present
Xlib:  extension "XFree86-DRI" missing on display ":0.0".
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
```

Thanks!

---

### Post by darrenm on 2007-01-04
I don't know why its saying texture from pixmap is present, if you are using ATi's proprietry fglrx driver then they don't support GLX_Texture_from_pixmap and can't be used with AIGLX...

I assume you are on Edgy and have disabled composite to allow the ATI drivers to work?

If not can you run fglrxinfo and post the output?

---

### Post by raul_ on 2007-01-04
Did you create a separate XGL session?

---

### Post by Nvening on 2007-01-04
TBH, i dont know, i followed a guide. Heres the output:

A Linux/UNIX instant messenger client, which can handle multiple protocols, including AIM, ICQ, Yahoo!, Jabber, and Gadu-Gadu.

And here is the guide i followed

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX)

The XGL guide said install it with AIGLX on Edgy

Thanks!!

EDIT: Just noticed this:

> Please note: ATI Cards : Depending on your card you may find that you can use the ati/radeon driver with AIGLX. If you experience problems then you may need to use Xgl with the fglrx Driver.

---

### Post by raul_ on 2007-01-04
For the drivers:
[http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide#C")

For Beryl:
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL]("http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL")

Let us know if it worked ;)

---

### Post by Nvening on 2007-01-04
But do i need to uninstall my installation first?

---

### Post by raul_ on 2007-01-04
Yes, you may want to undo the changes to your xorg.conf and so...

---

### Post by Nvening on 2007-01-04
Well do i need to, what will they do?

However, i think i have messed this up lol

On the driver installation i missed out a configuration command ](*,) 

This one:

sudo aticonfig --overlay-type=Xv

and rebooted, when i tried to verify the installation i got this:

nvening@Nvening-Ubuntu:~$ display: :0.0  screen: 0
bash: display:: command not found
nvening@Nvening-Ubuntu:~$ OpenGL vendor string: ATI Technologies Inc.
bash: OpenGL: command not found
nvening@Nvening-Ubuntu:~$ OpenGL renderer string: RADEON 9600 Generic
bash: OpenGL: command not found
nvening@Nvening-Ubuntu:~$ OpenGL version string: 2.0.6011 (8.28.8)
bash: syntax error near unexpected token `('

So i tried what it said a tried to revert back to the xorg driver however im not too sure if that did anything!

I feel like such an idiot now lol!

Oh and when i try and run the configuration now it says:
Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-4

Thanks for your help!!

---

### Post by raul_ on 2007-01-04
Just start all over again ;) 

> Next, find the Section "Device" for your graphics card, and add the following:

Option  "XAANoOffscreenPixmaps" **Delete this line**

And finally, add the following to the bottom of the file, unless it already exists elsewhere:

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable" ** Change to "Disable" **
EndSection


And then install fglrx again from the beginning (don't worry if the packages are already installed, it's just to make sure you didn't skip any more steps)

---

### Post by Nvening on 2007-01-04
Ok i did both of those guides and rebooted. However if i try and start beryl from command line i get this:

nvening@Nvening-Ubuntu:~$ beryl
XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present
beryl: No composite extension

:-k 
](*,) 

:mrgreen:

---

### Post by raul_ on 2007-01-04
Did you log in the Xgl session?

---

### Post by Nvening on 2007-01-05
No, i setup it up but i couldnt see any option on the login page. Ill have a closer look later but i have to do some "work now" ;)

---

### Post by raul_ on 2007-01-05
Make sure you have a separate Xgl session, otherwise Beryl won't load. Recheck the steps again.

 Keep up the good "work" ;)

---

### Post by Nvening on 2007-01-05
Yep, its all installed and confuigured nicely, great help from here and from #ubuntu-xgl too!

Many Thanks!!!

---

