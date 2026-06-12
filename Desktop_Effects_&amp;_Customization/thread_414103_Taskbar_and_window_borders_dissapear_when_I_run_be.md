---
title: "Taskbar and window borders dissapear when I run beryl"
date: 2007-04-19
forum: Desktop Effects &amp; Customization
---

### Post by Crashing on 2007-04-19
First, I would say that I have read the stickys and some other treads about beryl problems.
My computer has:
AMD Athalon 1 GHz processor
440 mb of ram
ATI Rage 128 graphics card
Kubuntu 7.04 (BIIIIIGGGGG Kudos to the ppl who developed this awesome distro!!!!)
As the subject says, whenever I run beryl, the window borders AND the taskbar disappear. Also, I can't right click to make the service menu come up and I can't type in any text anywhere. Using the "windows" key on the keyboard won't bring up the K-menu.
I tried using Konsole to run Beryl and got this gibberish:
```
josh@ThinkTank:~$ beryl-manager
josh@ThinkTank:~$ X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

(beryl-manager:6542): Gtk-CRITICAL **: gtk_check_menu_item_set_active: assertion `GTK_IS_CHECK_MENU_ITEM (check_menu_item)' failed
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Root visual is not a double buffered GL visual
beryl: Root visual is not a double buffered GL visual
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0
```
I have had the same problems when I tried beryl on Mandriva and OpenSUSE, but when it did those things, it wouldn't be reversible so I had to reinstall the OS. THis is the closest I've ever got to making Beryl work. I can run the Emerald theme manager fine and the Settings Manager.  I tried disabling all the 3d and animation effects because I really didn't want them and though that Beryl might be overtaxing my system. I found a thread where someone had the disappearing window borders problem and fixed it with the command: ```
emerald --replace &
```
Nothing has worked. Any suggestions??](*,) ](*,)

---

### Post by Shed on 2007-04-19
I find this, too :confused: .

---

### Post by m.musashi on 2007-04-20
Same prblem but
```
emerald --replace &
```
causes emerald to start and window decorations appear.

However, I get this message
```
(emerald:6468): Gdk-CRITICAL **: gdk_drawable_unref: assertion `GDK_IS_DRAWABLE (drawable)` failed
```

I also noticed that I don't have the beryl gem in my system tools as I used to under edgy and when beryl launches there is no gem on the task bar.

---

### Post by Crashing on 2007-04-21
Can anyone help us? I'd post this on the beryl forums, but nobody ever uses that forum.

---

### Post by m.musashi on 2007-04-21
I managed to solve the problem but I don't know if it's a universal solution or not. I installed the beryl package from the repo and it did not pick up the emerald dependencies nor did it install beryl-manager. Once I installed the emerald metapackage and beryl-manager it worked. Although I had also did "emerald --replace &" before so I don't know if that is part of the fix or not.

---

### Post by Crashing on 2007-04-21
I have installed most all of the Beryl/Emerald packages that I could get except for the developer ones and the ones specifically for GNOME and it doesn't work.

---

### Post by m.musashi on 2007-04-21
Oh, you are using KDE? Sorry, didn't see that. Although I don't think it should make much difference. However, there is a kubuntu package for beryl. I don't know how it's different. I have beryl on my desktop (feisty from beta and KDE) and I never had any problems - although the little bouncy gem on the mouse goes for about a minute but beryl itself loads quickly.

Post the contents of your xorg.cong (/etc/X11/xorg.conf).

It's possible the problem is related to either the ATI card and/or driver.

---

### Post by djrobthaman on 2007-04-22
I used to have this problem as well and I found that my problem was that I needed to log in to a session that loaded the xgl server.  So maybe that's you're problem.  So make sure you're loading whichever composite server you installed.

---

### Post by Crashing on 2007-04-23
> **djrobthaman said:**
> I used to have this problem as well and I found that my problem was that I needed to log in to a session that loaded the xgl server.  So maybe that's you're problem.  So make sure you're loading whichever composite server you installed.
I'd try that, but the login menu only has the options:
Session type:
>Default (previous)
>KDE
>Failsafe
Switch user
Restart X server
Console login
Shutdown
I don't know if it automatically uses the XGL server or not. is there a way to tell?

---

### Post by m.musashi on 2007-04-23
There is a way to create an XGL session as part of your login options. I don't know the details but it's part of one of the many beryl/XGL how-tos. For what it's worth, my attempt at this failed misserably. I have since given up on beryl on my ATI laptop.

---

### Post by m.musashi on 2007-04-25
I managed to re-create this problem - though it wasn't on purpose. I reconfigured the xserver and after that nothing I did would get emerald to work. I ended up reinstalling and then everything worked fine again.

I'm not sure how useful that info is but to me it suggests that some xserver setting is the cause and it was changed to a not good setting when I reconfigured.

Lesson: Don't reconfigure unless you know what you are doing - which I obviously didn't. However, reinstalling Ubuntu is a piece of cake.

---

### Post by keyboardduder on 2007-06-07
I try to run beryl or beryl - manager and they kill my title bars. reloading x server (Ctrl + alt + del) always makes it go back to normal. I have a 

Ubuntu 7.04 feisty fawn official release (all updates)
Pentium D 940
1 GB ddr2 dual channel
geforce 7600gs video card (probably the problem)
Biostar 945p neo 2 board

here is the code that i get, it just stop working at the (reloading options). And help would be greatly appreciated thanks.


colin@colin-desktop:~$ beryl
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Relaunching beryl with __GL_YIELD="NOTHING"
**************************************************************
* Beryl system compatiblity check                            *
**************************************************************

Detected xserver                                : NVIDIA

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : passed
Checking maximum texture size                   : passed (4096x4096)

Reloading options

---

