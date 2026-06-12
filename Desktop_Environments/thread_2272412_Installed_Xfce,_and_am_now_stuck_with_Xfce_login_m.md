---
title: "Installed Xfce, and am now stuck with Xfce login manager"
date: 2015-04-06
forum: Desktop Environments
---

### Post by Travis_Rector on 2015-04-06
I apologize if this has already been posted, but I couldn't find it. Everything I've tried on this issue doesn't work. 

I installed Xfce the other day, and it changed my login screen from Unity's to Xfce's, as you can see below: (Sorry for the pic, I couldn't take a screenshot of the login screen)
 [ATTACH=CONFIG]261124[/ATTACH]

I wish to get the default login screen back, but I cannot figure it out. I've tried editing the lightdm.conf file, but it's blank and when I add the lines that other posts have said, it forces Ubuntu into a low graphics mode. Is their anyway to get it back than what I've tried? Also, I've removed all of Xfce in an attempt to fix it, but that obviously didn't work. 

Thanks

---

### Post by egeezer on 2015-04-06
Look in the upper right-hand corner, there's a power icon there.  Either it or the icon next to it (can't remember what it looks like) will give you a drop-down where you can choose to go back to Unity.

Not that I ever leave Xfce, myself...  ;-)

---

### Post by Travis_Rector on 2015-04-06
Oh, no that's not the issue. I'm able to switch between them just fine (I now only have Unity, KDE, and Gnome installed, I may put Xfce back after I figure this out). My issue is the login screen. I liked the style of the default login screen when you first install Ubuntu:
[ATTACH=CONFIG]261142[/ATTACH]
No matter what I seem to try, I'm stuck with the Xfce login screen. It's alright though. It won't kill me to stay with that one, just wish I knew how to change it.

---

### Post by CantankRus on 2015-04-07
Xfce uses and installs the "lightdm-gtk-greeter" which overrides the unity-greeter.
Uninstall ...
```
sudo apt-get remove lightdm-gtk-greeter
```
Reboot.

---

### Post by Bucky Ball on 2015-04-07
You did just install xfce4 rather than xubuntu-desktop? If you just want the desktop environment, the former is the way to go. ;)

---

### Post by Travis_Rector on 2015-04-07
> **CantankRus said:**
> Xfce uses and installs the "lightdm-gtk-greeter" which overrides the unity-greeter.
Uninstall ...
```
sudo apt-get remove lightdm-gtk-greeter
```
Reboot.

Thanks a lot! That worked perfectly! Now I know for next time. Hopefully someday I'll know a lot more about Ubuntu and Linux in general.

> **Bucky Ball said:**
> You did just install xfce4 rather than  xubuntu-desktop? If you just want the desktop environment, the former is  the way to go. :wink:

Yeah, I did. I've been installing different desktop environments to see which I like best. Right now, I like Unity, KDE, and Xfce. Lxde was just too minimal for me. I was trying Mate yesterday, but now it freezes as soon as I login, so I don't know what the problem is there. :mad:

---

