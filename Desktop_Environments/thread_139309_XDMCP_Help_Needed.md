---
title: "XDMCP Help Needed"
date: 2006-03-03
forum: Desktop Environments
---

### Post by soongwoo on 2006-03-03
Problem: after successful login from gnome login screen in CygwinX window,
Ubuntu Desktop backgroud - Ubuntu Lagoon - is appeared more than 10 min time.

I've been using XDMCP as remote desktop with CygwinX on Windows platform.
The Linux Distro is FC4. Not Ubuntu.

I configured XDMCP as FC4, but failed. The symptom is "Problem".

I rather show what I did and should ask people for fixing the "Problem".

0) Prerequites: install necessary packages:
```
sudo apt-get install xfs xdm
```

1) Configure xfs: let xfs listen TCP port 7100
 - edit /etc/init.d/xfs and change the line:
```
start-stop-daemon --start --quiet $SSD_START_ARGS -- -daemon \
```
  to
```
start-stop-daemon --start --quiet $SSD_START_ARGS -- -droppriv -daemon -port 7100 \
```

 - edit /etc/X11/fs/config and change the line:
```
no-listen = tcp
```
  to
```
# no-listen = tcp
```

 - and then restart xfs:
```
sudo /etc/init.d/xfs restart
```

2) Configure xdm:
 - check files attributes:
```
/etc/X11/xdm/XServers   444
/etc/X11/xdm/Xaccess    644
/etc/X11/xdm/Xsetup_0   755
```

 - edit /etc/X11/xdm/xdm-config and change the line:
```
DisplayManager.requestPort:                         0
```
  to
```
! DisplayManager.requestPort:                       0
```

 - edit /etc/X11/xdm/Xaccess and change the line:
```
#*      # any host can get a login window
```
  to
```
*       # any host can get a login window
```
  and change this line, too:
```
#*      CHOOSER BROADCAST       #any indirect host can get a chooser
```
  to
```
*       CHOOSER BROADCAST       #any indirect host can get a chooser
```

3) Configure gdm: edit /etc/gdm/gdm.config
 - change the line in [security] section:
```
DisallowTCP=true
```
  to
```
DisallowTCP=false
```

 - change the line in [xdmcp] section:
```
Enable=false
```
  to
```
Enable=true
```

```
#Port=177
```
  to
```
Port=177
```

```
#Willing=/etc/gdm/Xwilling
```
  to
```
Willing=/etc/gdm/Xwilling
```

 - create a symbolic link to Xwilling:```
sudo ln -s /etc/X11/xdm/Xwilling /etc/gmd/Xwilling
```

4) Configure X86: edit /etc/X11/xorg.conf
 - add the line in Section "Files":```
FontPath        "unix/7100"
```

5) Restart X:
 - Just log off, and press Ctrl-Alt-Backspace at the login screen.
   This will kill X (the GUI), and it will automatically restart.

After do 5 spteps in Ubuntu box, I ran the following command in Cygwin console:
```
xwin -query ubuntu
```
Say, ubuntu is the name defined in /etc/hosts under Windows XP.

Then, nice GTK+ Greeter is showing in another CygwinX window. But after pressing
return with ID and password, it takes long time to show Ubuntu Desktop backgroud,
- Ubuntu Lagoon. Even worse, there is no panel in top and bottom of the screen.

Is there anyone to know what's wrong with this configuration?
Help needed to fix this problem and appreciate detailed explanation if possible.

Thanks
soongwoo

---

