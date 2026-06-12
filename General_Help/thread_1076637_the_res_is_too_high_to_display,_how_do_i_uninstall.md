---
title: "the res is too high to display, how do i uninstall catalyst from root?"
date: 2009-02-21
forum: General Help
---

### Post by Thowsen on 2009-02-21
hello,
my problem is that when i access ubuntu my monitor cant display because the screenres or the hertz are to high. I messed up with catalyst and now i need to either get into safe graphics mode or uninstall catalyst from the menu i get to when i press esc while the computer is bootin.
could someone please help me?

---

### Post by RedSingularity on 2009-02-21
Go to system>administration>hardware drivers.  Then click you graphics driver and Deactivate.

---

### Post by Thowsen on 2009-02-21
> **Shadow121 said:**
> Go to system>administration>hardware drivers.  Then click you graphics driver and Deactivate.
i cant even get to the log in screen now. my lcdmonitor wont display the res

---

### Post by RedSingularity on 2009-02-21
Can you boot into the TEXT login area?  CTL+ALT+F1 at login screen.

---

### Post by Axanon on 2009-02-21
If the resolution is too high to display you don't necessarily need to uninstall the drivers, it may be as simple as editing your xorg.conf file to change your default resolution. There is lots of help on setting up default display settings. I suggest you look for it, however it involves setting up your xorg.conf in this type of way:

```

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Samsung SyncMaster 920NW"
        Device          "NV11 [GeForce2 MX/MX 400]"
        Defaultdepth    24
        Option          "AddARGBGLXVisuals"     "True"

        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1280x1024" "1280x960" "1024x768" "800x600"
                Viewport        0 0
        EndSubSection
EndSection

```
The order in which you set your modes (in SubSection "Display") will be used as listed. So if you wanted a default resolution of "1024x768", you would place that first in the 'Modes'.

Please be careful and modify these settings to something that suits your needs. **This is only an example**. I am by no means an expert.. please research your situation more, this is only a suggestion.

---

### Post by Thowsen on 2009-02-22
thanks for the help but i can not even reach the xorg, cuz i cant even get to the log in screen. the screen starts to flicker n then it dies. then the monitor display (from its own software) ''utanför intervallet) which means that either the hz or res is to high to display

---

### Post by Thowsen on 2009-02-22
need help man

---

### Post by farmdve on 2009-02-22
I understand what you mean..many english people ignore the fact that you cant load your OS because your resolution is too high
I think when you restart your pc you can choose between the standard ubuntu and the text one thus if you choose the text one you will only need to execute a few commands which i dont know thats why people here should tell you!

---

### Post by Thowsen on 2009-02-22
> **farmdve said:**
> I understand what you mean..many english people ignore the fact that you cant load your OS because your resolution is too high
I think when you restart your pc you can choose between the standard ubuntu and the text one thus if you choose the text one you will only need to execute a few commands which i dont know thats why people here should tell you!
ehm , i can reach that system screen where i can choose either to repair broken dpkg files or fix xorg . n i've already tried to fix via that test.
but ubuntu cant find any errors so it keeps normal boot.
i need someone to tell me how to load safegraphicmode or something like that.
when it was blackened i tried the ctrl+alt+f1 with no success

---

### Post by RedSingularity on 2009-02-22
Here try [THIS]("http://ubuntuforums.org/showthread.php?t=438486")

---

### Post by [TCK] on 2009-02-22
Boot into recovery mode, select root (or whatever the command above xfix is), then type "nano /etc/X11/xorg.conf".  It's not user friendly, but hopefully nano should be up to the job.

Or if you have a backup in the X11 folder (you possibly do even if you've never intentionally done so) try replacing the xorg.conf file with that by typing "cp /etc/X11/xorg.confbackupfilename /etc/X11/xorg.conf".

---

