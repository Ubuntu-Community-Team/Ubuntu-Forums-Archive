---
title: "Beryl with XGL on Edgy with fglrx"
date: 2007-03-03
forum: Desktop Environments
---

### Post by Lafie on 2007-03-03
I seem to have a unique problem, which is frustrating me enormously.

I want to use Beryl with XGL on Edgy together with the fglrx drivers. I choose for XGL, because AIGLX doesn't work well with fglrx. 
XGL is installed and running properly, Beryl is also installed, but doesn't run properly.
When I run the beryl-xgl I get the following 'error':
> Detected xserver                                : AIGLX

I figured I AIGLX was still running and I found out that with Edgy it is automatically supported in Xorg. I would like to disable it and found out that this is what I have to add to xorg.conf:
> Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection
I added that to xorg.conf and did a couple of restarts, but running the command beryl-xgl still states that the Detected xserver is AIGLX, and now I don't know what to do anymore...

Any help is greatly appreciated. Thanks in advance.

---

### Post by lemoniceblock on 2007-03-05
You can [create a separate XGL session ]("http://http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/XGL#Adding_an_Xgl_login_session") and set that as your default session when logging in.

---

### Post by felyduw on 2007-03-05
I have exactly the same error.

I'm running fglrx (ati dual-head):
```
$ fglrxinfo 
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON 9600 XT
OpenGL version string: 2.0.6334 (8.34.8)
```

And I get:
```
$ beryl
**************************************************************
* Beryl system compatibility check                           *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : failed

No composite extension
beryl: No composite extension
```

Probably due to this:
```
$ /usr/bin/startxgl 

Fatal server error:
no screens found
```

Which has this code
```
$ cat /usr/bin/startxgl
Xgl -fullscreen :1 -ac -accel glx:pbuffer -accel xv:pbuffer & sleep 2 && DISPLAY=:1 
# Start GNOME
exec gnome-session
```

Hopefully someone will be able to help us

---

### Post by Deasuratae on 2007-03-05
Ok... I need to ask a question too, and this saves me making a new thread... I have been working with Ubuntu for almost a week... I am running an ATI Radeon 9200 SE (RV280). I have tried to install fglrx in several ways.... firstly, I tried the tutorial on one site for creating my own entry for it and so on... then I tried to install it with instructions on the beryl site... first time was that the splash screen just wouldnt load... so I reformatted.... then when I tried running the xgl session it would come up all funky, but gnome would run fine...


Now I have installed it using Beryl's auto install script... I rebooted, and now it says that X Windows will not run as there is a fatal error, no screen devices or something... It will not let me log into Ubuntu, but it will let me run the Recovery mode, I have no idea what to do from here... I have no problem reformatting and installing ubuntu again... but can someone PLEASE tell me how to get fglrx to work with the Radeon 9200 SE?????

---

### Post by Jordan-D on 2007-03-09
maybe you aren't logged in a xgl session

i have ATI X1600 XT and i was getting the same message when i was running a "gnome" session. When i switched to xgl session at the login screen and when i type beryl in the terminal i get a different message  :

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0

well this is another problem but it's a different message :)

---

### Post by bdogg64 on 2007-03-09
> **Jordan-D said:**
> maybe you aren't logged in a xgl session

i have ATI X1600 XT and i was getting the same message when i was running a "gnome" session. When i switched to xgl session at the login screen and when i type beryl in the terminal i get a different message  :

**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : XGL

Checking Display :1.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :1.0

well this is another problem but it's a different message :)

You should try "beryl --use-copy" instead if you texture_from_pixmap is missing

---

### Post by rob_jewkes on 2007-03-10
As as far as i am aware after reading a lot of forums and other stuff on the net ATI drivers do not yet support the 'Composite'  extension or at least not at the same time as running hardware acceleration, i believe ATI are working on this issue.
I have tried many different ways to run Beryl on my notebook with ATI graphics but to no avail.

Heres a snippet from my current xorg.conf :-

```

Section "Device"
    Identifier    "ATI Technologies, Inc. ATI Default Card"    
    Driver        "fglrx"
    BusID        "PCI:1:0:0"
EndSection

Section "Extensions"
    Option "Composite" "0"
EndSection
```

This gives me a working display with hardware acceleration, notice the last section:-

```

Option "Composite" "0"
```

This turns off composite mode, if i re-enable it by removing this section i get no hardware acceleration at all :(

So as it stands at the moment with ATI cards you can't run composite and have hardware acceleration together, therefore no Beryl :(

Hope ATI sort this problem out soon

Rob

---

### Post by sjrixon on 2007-03-10
Using it fine here with that setup :) I have an X1300...

Stick these two line in the session startup program box and away it goes..
```

beryl-manager --no-force-window-manager
beryl-xgl --use-copy
```

I would test if first before you stick it in startup ;)

Need anymore info and I would need some error messages.. But you are correct in turning of composite mode.

Scott
With a happy spinning cube!

---

