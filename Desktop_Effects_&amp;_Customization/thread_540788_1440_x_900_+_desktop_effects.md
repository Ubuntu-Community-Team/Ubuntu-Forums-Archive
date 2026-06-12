---
title: "1440 x 900 + desktop effects?"
date: 2007-09-02
forum: Desktop Effects &amp; Customization
---

### Post by grayfox444 on 2007-09-02
I'm new at Linux but I'm starting to understand it and get the hang of it, but there's something I still can't figure out.
Before I changed settings around to get the 1440 x 900 resolution, the desktop effects worked fine.  But since I've changed, they don't work properly.  To get the windows to "wobble" I have to hold a certain key down, and before I didn't.
Does anyone know how to fix this? 

Thanks.

---

### Post by michael37 on 2007-09-02
> **grayfox444 said:**
> I'm new at Linux but I'm starting to understand it and get the hang of it, but there's something I still can't figure out.
Before I changed settings around to get the 1440 x 900 resolution, the desktop effects worked fine.  But since I've changed, they don't work properly.  To get the windows to "wobble" I have to hold a certain key down, and before I didn't.
Does anyone know how to fix this? 

Thanks.

I have a laptop wtih 1440x900 resolution and desktop effects including wobbly windows work fine for me.  What is this "certain key"?   Have you poked around in the "Wobbly Windows" plugin in the CompizConfig Setting Manager (it's under System/Preferences).

---

### Post by grayfox444 on 2007-09-03
Well it only lets me use it if I'm holding down the Cntl, Alt, or Win key. And I can't see that item under System/Prefs.

---

### Post by michael37 on 2007-09-03
To help us understand the problem, could you please run through the questions in [thread=537836]this post[/thread]?

---

### Post by grayfox444 on 2007-09-03
Section "Device"
        Identifier      "GeForce 7300"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
        VideoRam        256000
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "ViewSonic VX1935wm"
        Option          "DPMS"


direct rendering: Yes
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce 7300 GT/PCI/SSE2
OpenGL version string: 2.1.0 NVIDIA 96.31
OpenGL extensions:

grep AIGLX /var/log/Xorg.*.log  = did not return anything.


ii  compiz                                     0.3.6-1ubuntu13                        OpenGL window and compositing manager
ii  compiz-core                                0.3.6-1ubuntu13                        OpenGL window and compositing manager
ii  compiz-gnome                               0.3.6-1ubuntu13                        OpenGL window and compositing manager - GNOM
ii  compiz-gtk                                 0.3.6-1ubuntu13                        OpenGL window and compositing manager - Gtk 
ii  compiz-plugins                             0.3.6-1ubuntu13                        OpenGL window and compositing manager - plug
ii  libdecoration0                             0.3.6-1ubuntu13                        Compiz window decoration library

---

### Post by michael37 on 2007-09-03
Hello, let me guide you to a few how-tos that you may find very helpful.

[LIST=1]
[*]How to enable AIGLX and composite for your Nvidia video card. [https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy]("https://help.ubuntu.com/community/CompositeManager/AIGLXOnEdgy") You need it in order to turn on most 3D effects.
[*]Remove old (and no longer supported) compiz version 0.3.6 that you are still running in order to prepare installing new CompizFusion.
```

      sudo apt-get --purge remove compiz* libcompizconfig0 libdecoration0
      sudo aptitude remove libgnome-compiz-manager0 compiz-extra libcompizconfig0 compiz-dev compiz-gtk compiz-kde compiz-settings libcompizconfig-backend-gconf compiz-config-ini gcompizthemer compiz-plugins libgnome-compiz-manager-dev compizconfig-backend-kde compizconfig-settings-manager python-compizconfig compiz-config-gnome taskbar-compiz compizconfig-plugin compiz-freedesktop-dev compiz-fusion-plugins-unofficial compiz-bcop compiz-ccs-settings-manager libgnome-compiz-manager libcompizconfig0-dev compiztools compizconfig-settings-legacy compiz-fusion-plugins-extra compiz-compcomm-plugins-main compiz-fusion-plugins-unsupported compiz compiz-extra-plugins compiz-fusion-plugins-main libcompizconfig-backend-kconfig compiz-core compiz-decorator gnome-compiz-manager compiz-fusion-plugins-main compiz-gnome libcompizconfig-dev libgnome-compiz-manager0-dev libcompizconfig0 libcompizconfig-backend-gconf libcompizconfig0-dev libcompizconfig-backend-kconfig libcompizconfig-dev

```
[*]Install Compiz Fusion. [https://help.ubuntu.com/community/CompositeManager/CompizFusion]("https://help.ubuntu.com/community/CompositeManager/CompizFusion")
[/LIST]

---

### Post by grayfox444 on 2007-09-03
I've done steps 1 and 2, but I don't understand the two deb lines.

---

### Post by michael37 on 2007-09-04
> **grayfox444 said:**
> I've done steps 1 and 2, but I don't understand the two deb lines.

I take you are talking about two deb lines in step 3?  Those are repositories.  A great overview is [on this page](https://help.ubuntu.com/community/Repositories), continue with "Managing Repositories in Ubuntu" link from that page.

Since you are on this forum, I recommend enabling Universe and Multiverse standard repositories as well.

---

### Post by grayfox444 on 2007-09-04
Yeah that's what I'm talking about, but I don't have that item under my System/Prefs menu, and if I enter "/etc/apt/sources.list " into the terminal it says access denied.

---

### Post by psyopper on 2007-09-04
> **grayfox444 said:**
> Yeah that's what I'm talking about, but I don't have that item under my System/Prefs menu, and if I enter "/etc/apt/sources.list " into the terminal it says access denied.

It's in System -> Administration -> Software Sources

If you want to edit manually you should try
```
sudo gedit /etc/apt/sources.list
```

Sudo gives you Super User (administrator) rights, gedit is the application you will open the file with (like notepad in Windows), then the file you want to open.

Good luck!!

---

### Post by grayfox444 on 2007-09-05
I don't see the Add buttons, my tabs are different than the ones shown in the images. I have: Ubuntu Software, Third Party Software, Updates, Authentication, Updates.

---

### Post by psyopper on 2007-09-05
> **grayfox444 said:**
> I don't see the Add buttons, my tabs are different than the ones shown in the images. I have: Ubuntu Software, Third Party Software, Updates, Authentication, Updates.

Use the "Third Party Software" tab. In the lower left there is a button for "Add". When you click it there will be a dialog box for you to enter the line(s). See the attachment below...

This is an excellent example of where using the terminal window and/or editing the file itself is actually easier than using the GUI.

---

### Post by grayfox444 on 2007-09-05
Okay I now have everything installed and I'm able to reach the Compiz settings through System/Prefs, now how do I get them working? I have the boxes checked.
Though System/Prefs -> Desktop Effects is no longer there.

---

### Post by grayfox444 on 2007-09-05
I got them working, thanks for your help everyone.

Just one last thing, the update manager won't go away, it's telling me there's a new update for compiz but even if i install it it is still there.
Also, how do I zoom out and look at that desktop cube? It just see,s to be rotating on a 2D plane

---

### Post by grayfox444 on 2007-09-05
I tried right clicking the "switch desktops" on the bottom right corner and going to preferences and changing the number of desktops to 4.
But it didn't seem to do anything.

---

### Post by psyopper on 2007-09-06
> **grayfox444 said:**
> I got them working, thanks for your help everyone.

Just one last thing, the update manager won't go away, it's telling me there's a new update for compiz but even if i install it it is still there.
Also, how do I zoom out and look at that desktop cube? It just see,s to be rotating on a 2D plane

Go back into System -> Software Sources and uncheck the repositories you added. If they are unchecked the Update Manager will not look at them to see if they have updates available.

As for the cube... Open CompizConfig Settings Manager (CCSM) -> General -> Desktop Size:
Horizontal Virtual Size : 4
Vertical Virtual Size : 1
Number of Desktops : 1

Disregard the desktop chooser on your Gnome Panel. In fact, you can remove it.

Welcome to Compiz-Fusion!

---

### Post by grayfox444 on 2007-09-06
Thanks a ton! It works!
One last quick thing, how do you zoom out to see more of the cube rather than jsut the close up view?
I'm using cntrl+alt and dragging the mouse to move it.

---

### Post by JBAlaska on 2007-09-06
In CCSM, rotate cube plugin setting, You can adjust the zoom slider.

---

