---
title: "HELP? Problem when trying to get ready before installing BERYL"
date: 2007-05-13
forum: Desktop Effects &amp; Customization
---

### Post by Izaksly on 2007-05-13
im running an AMD64. I have a ATI Xpress 200M, and i was trying to get ready to install BERYL
when i used this How-to 

[http://ubuntuforums.org/showthread.php?t=399643&highlight=beryl+xgl+ati](http://ubuntuforums.org/showthread.php?t=399643&highlight=beryl+xgl+ati)

It didnt work.

So im using this one:

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

BUT I HAVE A PROBLEM :'( I GET THIS:
[COLOR="Blue"]
izaksly@izaksly-laptop:~$ glxinfo | grep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
izaksly@izaksly-laptop:~$ glxinfo | grep "direct rendering"
direct rendering: No[/COLOR]

And according to the how to, i should get a YES, what does that mean? and is it needed ? what exactly is it ? 

HELP!

---

### Post by lungdart on 2007-05-14
I found the instructions had some room for noobie error, which may have caused your problem. so follow these steps (basicly the same instructions again) and see if it helps. If not, your just right back where you started.

First I would verify that the right drivers are installed

```
sudo apt-get install libgl1-mesa-glx libgl1-mesa-dri
```

If there up to date, go ahead, if not install them and there dependancies.

Now replace your xorg.conf with its backup (If you didnt make a backup, and you used gedit to edit the file, it makes a backup for you luckily), and edit the backup again.

```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf_OLD
sudo cp /etc/X11/xorg.conf~ /etc/X11/xorg.conf
sudo gedit /etc/X11/xorg.conf

```

in the file you want to find the section that says

```

Section "Device"
        xxxxxx
        Driver                "ati"
        xxxxxxxxxx
EndSection

```

and replace the driver line so it looks like this. LEAVE ALL OTHER LINES ALONE (the x's represent the lines that are already there. They are the ones you do not want to change. The extra lines after the x's are lines you append to that section)

```

Section "Device"
        xxxxxx
        Driver                "radeon"
        xxxxxxxxxx
        Option          "XAANoOffscreenPixmaps"
        Option "AGPMode" "4"
        Option "AGPFastWrite" "true"
        Option "DisableGLXRootClipping" "true"
        Option "AddARGBGLXVisuals" "true"
        Option "AllowGLXWithComposite" "true"
        Option "EnablePageFlip" "true"
EndSection

```

Also, you will want to find this section

```

Section "ServerLayout"
        xxxxxx
EndSection

```

and add this line to the section

```

Section "ServerLayout"
        Option          "AIGLX"         "true"
        xxxxxx
EndSection

```

And finally you want to add to the end of the file, these lines.

```

Section "DRI"
        Mode 0666
EndSection

Section "Extensions"
        Option "Composite" "Enable"
EndSection

```

After all that is done restart your x server or reboot your computer. when it comes back up try your grep commands again to see if it says direct rending: yes. If your the x server fails you can just replace the new xorg.conf file you made with xorg.conf_OLD, and reboot.

Good luck

---

