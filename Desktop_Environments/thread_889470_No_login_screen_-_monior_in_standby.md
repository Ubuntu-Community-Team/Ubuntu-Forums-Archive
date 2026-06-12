---
title: "No login screen - monior in standby"
date: 2008-08-14
forum: Desktop Environments
---

### Post by sirHC88 on 2008-08-14
Hi all!

I've got a problem with the GUI of my Ubuntu Hardy that should run as an LTSP-server on an IBM System x3650. The system boots normally but after it finishes loading the login screen doesn't appear. Instead the monitor goes in standby-mode.

I am able to use the console with Ctrl+Alt+F1-F6. I am also able to access the LTSP-server with ssh -X (except for one time, I had to delete the "/home/vl/.Xauthority" which was recreated immediately and worked afterwards).

I have already tried "sudo apt-get install --reinstall ubuntu-desktop" with no success. When trying "sudo dpkg-reconfigure -phigh xserver-xorg" I get "md5sum: /etc/X11/xorg.conf: No such file or directory" although it is there. :confused:

Any ideas how to get back the GUI?

Help very much appreciated.

---

### Post by sirHC88 on 2008-08-19
Hey all,

I've got it working so far.:guitar:

I don't know how I did it exactly, but i think it has something to do wit installing Envy, which did not work. Then i removed it and suddenly had my xorg.conf modified. Now it looks like that:

```

...
Section "Device"
        Identifier      "Configured Video Device"
        Boardname       "vesa"
        Busid           "PCI:1:6:0"
        Driver          "vesa"
        Screen  0
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Configured Video Device"
        Monitor         "Configured Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 640     480
                Modes           "640x480@60"
        EndSubSection
EndSection
...

```

As you can see I've got quite a low resolution now. Can anyone tell me what I have to change to be able to choose higher resolutions or show me kinda tutorial.

Thanks.

---

