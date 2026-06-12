---
title: "Strange behavior after changing monitor driver"
date: 2007-12-28
forum: Desktop Environments
---

### Post by sjoseph on 2007-12-28
Hi All,

After changing my video driver from 'Plug and Play' to the NVDIA driver (to decrease screen flutter) and trying different resolutions, the system is acting funny. I lost the min/max and quite buttons on all title bars as well as double clicking function on title bar to maximize. I also get a blank box when I open Terminal. These are the only problems that I have discovered. What have I done.

Steve

---

### Post by overdrank on 2007-12-28
> **sjoseph said:**
> Hi All,

After changing my video driver from 'Plug and Play' to the NVDIA driver (to decrease screen flutter) and trying different resolutions, the system is acting funny. I lost the min/max and quite buttons on all title bars as well as double clicking function on title bar to maximize. I also get a blank box when I open Terminal. These are the only problems that I have discovered. What have I done.

Steve

Hi and you may add these to your xorg
First back up your xorg
To copy Xorg
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```
To restore backup
```
sudo cp /etc/X11/xorg.conf.backup /etc/X11/xorg.conf
```
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
Edit your xorg with this command ```
gksudo gedit /etc/X11/xorg.conf
```

---

### Post by sjoseph on 2007-12-28
Thanks but one strange problem is that I can't even access Terminal in Gnome. How would I get to it otherwise.

---

### Post by overdrank on 2007-12-28
> **sjoseph said:**
> Thanks but one strange problem is that I can't even access Terminal in Gnome. How would I get to it otherwise.

Hi you can use the alt, F2 keys to run the command.

---

### Post by sjoseph on 2007-12-28
Sorry, I think you misunderstood. When I try to run Terminal, I just get a blank screen. Can I input these sudo commands in Alt-f2

---

### Post by overdrank on 2007-12-28
> **sjoseph said:**
> Sorry, I think you misunderstood. When I try to run Terminal, I just get a blank screen. Can I input these sudo commands in Alt-f2

Ok sorry not reading very well. I would use the virtual terminal to back up your xorg first. The keys alt, ctrl, F1. The to return to the GUI use the keys alt, ctrl, F7  and to edit your xorg command run in alt f2

---

### Post by sjoseph on 2007-12-28
where exactly do i add these 

Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"

---

### Post by overdrank on 2007-12-28
> **sjoseph said:**
> where exactly do i add these 

Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"

Duh :oops:  Sorry I must be slipping today. In the device section of the xorg
Example
Section "Device"
    Identifier     "nVidia Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
Option "AddARGBVisuals" "True"
Option "AddARGBGLXVisuals" "True"
EndSection

---

### Post by sjoseph on 2007-12-28
Thanks Overdrank,

This did the trick. Appreciate your help.

---

### Post by overdrank on 2007-12-28
> **sjoseph said:**
> Thanks Overdrank,

This did the trick. Appreciate your help.

No problem and sorry for leaving things out. I have several threads going and am getting lost lol. Please mark the thread solved under thread tools and good luck!

---

