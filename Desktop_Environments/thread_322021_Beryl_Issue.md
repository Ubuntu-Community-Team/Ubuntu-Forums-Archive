---
title: "Beryl Issue"
date: 2006-12-19
forum: Desktop Environments
---

### Post by shigidab0p on 2006-12-19
Hello

I decided to get Beryl after hearing so many good things about it.  I installed the correct driver for my graphics card which appears to be working fine.  However, when I run beryl, it just doesn't go and instead reverts back to regular knome style windows.  The terminal output is:

```
fitzmlj@fitzmlj-laptop:~$ beryl-manager
fitzmlj@fitzmlj-laptop:~$ XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: No composite extension
```

Does anybody have a solution? Thanks in advance.

---

### Post by rsambuca on 2006-12-19
Can you post your /etc/X11/xorg.conf please?

---

### Post by shigidab0p on 2006-12-20
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV17 [GeForce4 420 Go]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "ExactModeTimingsDVI"   "TRUE"
    Option         "ModeValidation"   "DPF-0: NoEdidDFPMaxSizeCheck, NoVesaModes"
# Enable 32-bit ARGB GLX Visuals
    Option "AddARGBGLXVisuals" "True"
 
# If you are using an older version of compiz that
# does not support rendering into the Composite
# Overlay Window, you will need to disable clipping
# of GLX rendering to the X Root window with this
# option, or you will get a blank screen after
# starting compiz:
    Option "DisableGLXRootClipping" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1024x768"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1024x768"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Disable"
EndSection
```

Thanks for the reply, sorry for taking so long.

---

### Post by d3v1ant_0n3 on 2006-12-20
```
Section "Extensions"
    Option         "Composite" "Disable"
EndSection
```

Shouldn't that be "Enable"? Or is that just for Intels?

---

### Post by torikulhasan@yahoo.com on 2006-12-20
Hello,

I m new in this forum. just registered few minutes ago.

I want to install the beryl repository:
I m following the procedures of the page:
       [http://64.233.161.104/search?q=cache:tA8C2BreX1EJ:wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX+beryl+dapper+install&hl=en&gl=ca&ct=clnk&cd=1&client=firefox-a](http://64.233.161.104/search?q=cache:tA8C2BreX1EJ:wiki.beryl-project.org/index.php/Install/Ubuntu/Dapper/AiGLX+beryl+dapper+install&hl=en&gl=ca&ct=clnk&cd=1&client=firefox-a)

applied the following command:

       sudo nano /etc/apt/sources.list

I added the following link in source.list as instructed in the page

      deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) dapper main aiglx

then applied following command

      sudo apt-get update

the outcome of this command is as:

Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper Release.gpg [191B]
Get:3 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates Release
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Packages
Hit [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) dapper/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release.gpg
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper Release
Ign [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Hit [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) dapper/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Fetched 194B in 9s (21B/s)
Failed to fetch [http://ubuntu.beryl-project.org/dists/dapper/Release](http://ubuntu.beryl-project.org/dists/dapper/Release)  Unable to find expected entry  aiglx/binary-i386/Packages in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.


CAN ANYBODY HELP ME IN THIS REGARD, TO COMPLETE THE INSTALLATION OF BERYL IN MY PC

Rgds,
Hasan

---

### Post by shigidab0p on 2006-12-20
Can anyone help?

---

### Post by ramjet_1953 on 2006-12-21
I have exactly the same problem, when I run sudu apt-get update.
Is there a new link?

Regards,
Roger :cool:

---

### Post by xabbott on 2006-12-21
> **ramjet_1953 said:**
> I have exactly the same problem, when I run sudu apt-get update.
Is there a new link?

Regards,
Roger :cool:

Maybe try these? I use Edgy and use the Edgy guides from this site. These are for dapper. If you use ATI+Fglrx use the XGL guide. Otherwise I think you want the AiGLX.

[http://wiki.beryl-project.org/wiki/Install/Ubuntu/Dapper/AiGLX](http://wiki.beryl-project.org/wiki/Install/Ubuntu/Dapper/AiGLX)

[http://wiki.beryl-project.org/wiki/Install/Ubuntu/Dapper/XGL](http://wiki.beryl-project.org/wiki/Install/Ubuntu/Dapper/XGL)

---

### Post by droth6666 on 2006-12-21
These are the repositories I used:

deb [http://beryl.lupine.me.uk](http://beryl.lupine.me.uk) dapper main
deb-src [http://beryl.lupine.me.uk](http://beryl.lupine.me.uk) dapper main

Not sure if they're still there.

---

### Post by lupine_nickt on 2006-12-22
It's ubuntu.beryl-project.org

For dapper, it's really not very good I'm afraid - you can browse the available packages by clicking the link

Trevinho's SVN repository has an i386 dapper section, so you could try that

xF,

...Nick

---

