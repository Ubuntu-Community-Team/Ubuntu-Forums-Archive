---
title: "[SOLVED] mouse disappears after logout"
date: 2007-10-15
forum: Debian
---

### Post by -grubby on 2007-10-15
OK so I'm using Debian Etch and This is a weid problem. I think it has to do with my download being corrupted but anyway, I've installed Debian on 3 different computers and they all have the same problem: I start Debian, I login, the mouse pointer is shown. When I log out the mouse  cursor disappears but I can still highlight and click things. When I login, the mouse still doesn't appear but I can click on things. I have to restart to fix this. I have tried different mice with the same problem. Any help would be greatly appreciated, thanks!
UPDATE: this happens with lenny too so I think it might be the xserver

---

### Post by -grubby on 2007-10-15
*bump*

---

### Post by RAV TUX on 2007-10-15
> **nathangrubb said:**
> OK so I'm using Debian Etch and This is a weid problem. I think it has to do with my download being corrupted but anyway, I've installed Debian on 3 different computers and they all have the same problem: I start Debian, I login, the mouse pointer is shown. When I log out the mouse  cursor disappears but I can still highlight and click things. When I login, the mouse still doesn't appear but I can click on things. I have to restart to fix this. I have tried different mice with the same problem. Any help would be greatly appreciated, thanks!

Does it happen with Ubuntu also or just in Debian?

__________________

[CENTER][IMG]http://ubuntuforums.org/attachment.php?attachmentid=46333&d=1192382949[/IMG][/CENTER]

---

### Post by -grubby on 2007-10-15
just debian.

---

### Post by -grubby on 2007-10-15
*bump*

---

### Post by -grubby on 2007-10-15
well.........no solution

---

### Post by -grubby on 2007-11-10
I'll have to bump this one because I reinstalled Debian again (same CD) and still have the same problem

---

### Post by rsambuca on 2007-11-12
Compare your xorg.conf files from ubuntu and debian.

---

### Post by -grubby on 2007-11-12
just one slight problem...I don't have ubuntu installed (on this computer)

---

### Post by rsambuca on 2007-11-12
Have you tried reconfiguring your xserver?

---

### Post by Caffeine_Junky on 2007-11-12
Hmm , interesting problem you got there bud.. I had a simular prob with gOS and this fixed it

Try adding the line I have marked in RED for the device section of xorg.conf.

```
Section "Device"
    Identifier     "nVidia Corporation C51G [GeForce 6100]"
    Driver         "nvidia"
   [COLOR="Red"] Option         "HWCursor" "off"[/COLOR]
```


and see if there is anything in my mouse section here that will fix it for ya..
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"  [COLOR="Red"]"true"[/COLOR]
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "false"
EndSection
```

I have used etch before, and it is a good stable OS, ...but as for Xorg..  ...meh, it has a mind of its own.

So, as was suggested previous to my post, a simple dpkg-reconfigure xserver-xorg from a terminal will probably do the job (eventually) :p

---

### Post by -grubby on 2007-11-12
> **rsambuca said:**
> Have you tried reconfiguring your xserver?

yes,several times

---

### Post by -grubby on 2007-11-12
> **Caffeine_Junky said:**
> Hmm , interesting problem you got there bud.. I had a simular prob with gOS and this fixed it

Try adding the line I have marked in RED for the device section of xorg.conf.

```
Section "Device"
    Identifier     "nVidia Corporation C51G [GeForce 6100]"
    Driver         "nvidia"
   [COLOR="Red"] Option         "HWCursor" "off"[/COLOR]
```


and see if there is anything in my mouse section here that will fix it for ya..
```
Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"  [COLOR="Red"]"true"[/COLOR]
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "false"
EndSection
```

where is the xorg.conf file?

---

### Post by Caffeine_Junky on 2007-11-12
sudo gedit /etc/X11/xorg.conf

---

### Post by rsambuca on 2007-11-12
> **Caffeine_Junky said:**
> sudo gedit /etc/X11/xorg.conf

You probably don't need sudo, unless you specifically added it in Debian.

---

### Post by -grubby on 2007-11-12
> **Caffeine_Junky said:**
> sudo gedit /etc/X11/xorg.conf

that file doesn't exist but under nautilus in /etc/x11 there is a file called "xorg.conf" but has some really weird numbers after it. Actually, there are two.

---

### Post by Caffeine_Junky on 2007-11-12
> UPDATE: this happens with lenny too so I think it might be the xserver

Yup, ... xorg and Xdebconfigurator in  [[COLOR="SeaGreen"]_gOS_[/COLOR] ]("http://www.thinkgos.com/index.html") gave me a hell of a time when trying to sort my monitor graphic's

---

### Post by Caffeine_Junky on 2007-11-12
> **nathangrubb said:**
> that file doesn't exist but under nautilus in /etc/x11 there is a file called "xorg.conf" but has some really weird numbers after it. Actually, there are two.

you are using GNOME in Lenny or KDE?


and the xorg.conf (with numbers after it) would be a Backup that xorg has created from doing the dpkg-reconfig* thing

---

### Post by -grubby on 2007-11-12
> **Caffeine_Junky said:**
> you are using GNOME in Lenny or KDE?


and the xorg.conf (with numbers after it) would be a Backup that xorg has created from doing the dpkg-reconfig* thing

GNOME. And yes I did do "dpkg-reconfigure xserver-xorg". Wait a minute I found xorg.conf

---

### Post by Caffeine_Junky on 2007-11-12
> **nathangrubb said:**
>  ...Wait a minute I found xorg.conf

cool, ... I knew there had to be one in there :p

---

### Post by -grubby on 2007-11-12
OK edited my Xorg.conf so I'm going to log out and see how it goes

---

### Post by -grubby on 2007-11-12
OK good news editing my Xorg.conf file fixed it!

---

### Post by Caffeine_Junky on 2007-11-12
WOOOOHOOOO!!!  :p

Glad to hear it worked for ya

---

### Post by rsambuca on 2007-11-12
Good stuff!

---

### Post by -grubby on 2007-11-12
> **Caffeine_Junky said:**
> WOOOOHOOOO!!!  :p

Glad to hear it worked for ya

I just backed up my xorg.conf so if I happen to have to reinstall I have a backup. Also doing that fixed some minor graphical glitches I was having

---

### Post by Caffeine_Junky on 2007-11-12
Yep's, backing up all that sort of stuff saves time if you have a similar problem sometime down the "distro hoping road"..

I keep all sorts of hint's and fixes I have found, ...I just copy'n'paste them into a text editor and save them, to my  USB-Thumb Drive.

---

### Post by ratthing on 2008-02-03
Just wanted to note for others searching: I had the same problem with Xubuntu Fiesty Fawn (debian_version is lenny/sid) on an Nvidia 6100 video card, but my cursor disappeared and then would not come back after a reboot.  Adding the two Xorg lines fixed it.

=RT=

---

### Post by addr1 on 2008-12-11
I found this with a Google search.

Actually using Xfce on Arch and this has been bugging me since installation.

> Option "HWCursor" "off"

fixed it for me.

How did you come up with that?

Thanks a lot!

---

