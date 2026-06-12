---
title: "Where to download various desktop environments from ?"
date: 2013-05-01
forum: Desktop Environments
---

### Post by arifalisyed on 2013-05-01
Hi 
    I have Xubuntu 13.04 and i want to try out different desktop environments  like 
[COLOR=#000000][FONT=verdana]
- Unity 6.6.0[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]- GNOME Shell 3.6.2[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]- GNOME Classic 3.6.2[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]- KDE Plasma 4.9.90[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]- Xfce 4.10[/FONT][/COLOR]
[FONT=verdana][COLOR=#000000]- LXDE 0.5.11[/COLOR][/FONT]

[FONT=verdana][COLOR=#000000]feel free suggest more if i have missed any :).[/COLOR][/FONT]

[FONT=verdana][COLOR=#000000]I couldn't find them in my synaptic Package manager.[/COLOR][/FONT]
[FONT=verdana][COLOR=#000000]perhaps i need to add their repository first.[/COLOR][/FONT]
[FONT=verdana][COLOR=#000000]but i dont their repository, it would be good if we could create a sticky thread here which contains the list of desktop environments and their repository links.
[/COLOR][/FONT]
following blog inspired me to try them all on my PC [Intel Pentium 4 , 2 Gig RAM , Intel 915 Motherboard]

---

### Post by matt_symes on 2013-05-01
> **arifalisyed said:**
> Hi 
    I have Xubuntu 13.04 and i want to try out different desktop environments  like 
[COLOR=#000000][FONT=verdana]
- Unity 6.6.0[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]- GNOME Shell 3.6.2[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]- GNOME Classic 3.6.2[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]- KDE Plasma 4.9.90[/FONT][/COLOR]
[COLOR=#000000][FONT=verdana]- Xfce 4.10[/FONT][/COLOR]
[FONT=verdana][COLOR=#000000]- LXDE 0.5.11[/COLOR][/FONT]

[FONT=verdana][COLOR=#000000]feel free suggest more if i have missed any :).[/COLOR][/FONT]

[FONT=verdana][COLOR=#000000]I couldn't find them in my synaptic Package manager.[/COLOR][/FONT]
[FONT=verdana][COLOR=#000000]perhaps i need to add their repository first.[/COLOR][/FONT]
[FONT=verdana][COLOR=#000000]but i dont their repository, it would be good if we could create a sticky thread here which contains the list of desktop environments and their repository links.
[/COLOR][/FONT]
following blog inspired me to try them all on my PC [Intel Pentium 4 , 2 Gig RAM , Intel 915 Motherboard]

Many are in the repos. 
```
matthew-S206:/etc/update-manager % apt-cache search 'tu-desktop'
ubuntu-desktop - The Ubuntu desktop system
mythbuntu-desktop - The Mythbuntu standalone system
edubuntu-desktop - educational desktop for Ubuntu
kubuntu-desktop - Kubuntu Plasma Desktop/Netbook system
lubuntu-desktop - Lubuntu Desktop environment
xubuntu-desktop - Xubuntu desktop system
```

You install them with

```
sudo apt-get install <package_name>
```

For gnome shell look at this link

[http://www.ubuntuupdates.org/ppa/gnome_3](http://www.ubuntuupdates.org/ppa/gnome_3)

You are also more than likely using [COLOR=#000000][FONT=verdana]Xfce 4.10 when using [/FONT][/COLOR]xubuntu.

```
matthew-S206:/etc/update-manager % xfwm4 --version              
        This is xfwm4 version 4.10.0 (revision cc70567) for Xfce 4.10
        Released under the terms of the GNU General Public License.
        Compiled against GTK+-2.24.14, using GTK+-2.24.17.

        Build configuration and supported features:
        - Startup notification support:                 Yes
        - XSync support:                                Yes
        - Render support:                               Yes
        - Xrandr support:                               Yes
        - Embedded compositor:                          Yes
        - KDE systray proxy (deprecated):               No
matthew-S206:/etc/update-manager % 
```

There are many more window managers, some floating, some tiling and some both. 

There is also a distinction between a window manager and a desktop environment.

Have a read of this.

[http://en.wikipedia.org/wiki/X_window_manager](http://en.wikipedia.org/wiki/X_window_manager)

If you want to try something a bit different then try a tiling window manager as well such as awesome. It can actually be used as both a tiling and floating window manager.

```
matthew-S206:/etc/update-manager % apt-cache search ^awesome
awesome - highly configurable X window manager
awesome-extra - additional modules for awesome
matthew-S206:/etc/update-manager %
```

**EDIT:**

You may want to add some more memory for the heavier window managers.

Kind regards

---

### Post by ibjsb4 on 2013-05-01
Gnome-Classic :D

```
sudo apt-get install gnome-session-fallback
```

---

### Post by matt_symes on 2013-05-01
Hi

Here are two more popular ones; openbox and enlightenment.

```
matthew-S206:/etc/update-manager % apt-cache search -- '^e17$'
e17 - Enlightenment DR17 Window Manager
matthew-S206:/etc/update-manager %  apt-cache search -- '^openbox' 
openbox - standards compliant, fast, light-weight, extensible window manager
openbox-dev - development files for the openbox window manager
openbox-themes - Themes for the Openbox window manager
openbox-xdgmenu - Xdg menu for OpenBox
matthew-S206:/etc/update-manager % 
```

Kind regards

---

### Post by Peripheral Visionary on 2013-05-01
It isn't really necessary to download the metapackages (kubuntu-desktop, xubuntu-desktop, etc) since they pull in much more than just the desktop environments.  You can simply install Xfce4, KDE, LXDE, etc without all that extra fluff.  However, the mixtures xubuntu-desktop, kubuntu-desktop, etc do include some awesome settings and configurations that make using the different desktops more fun!

---

### Post by Resistent on 2013-05-01
Your PC is very old, avoid Unity ! TAKE **ONLY** Leightweight !
Unity was a horror on my old Notebook with [Intel Celeron M 430 @ 1.73GHz]("http://www.cpubenchmark.net/cpu_lookup.php?cpu=Intel+Celeron+M+430+%40+1.73GHz&id=701") 

I am using now Lubuntu, this PC is a HP Compaq DC 7600 SFF ([COLOR=#000000][FONT=Arial]Intel Dual Core Processor 840, [/FONT][/COLOR][COLOR=#000000][FONT=Arial]Intel® 945G chipset
[/FONT][/COLOR]and works very good. [COLOR=#000000][FONT=Arial]


[/FONT][/COLOR]

---

### Post by matt_symes on 2013-05-01
Hi

> **Peripheral Visionary said:**
> It isn't really necessary to download the metapackages (kubuntu-desktop, xubuntu-desktop, etc) since they pull in much more than just the desktop environments.  You can simply install Xfce4, KDE, LXDE, etc without all that extra fluff.  However, the mixtures xubuntu-desktop, kubuntu-desktop, etc do include some awesome settings and configurations that make using the different desktops more fun!

Agreed and I'll elaborate for the OP.

@OP. I should make it clear that installing the meta-packages will install the applications that those desktop environments also use.

If you want to see what is included in the fully fledged desktop then install the meta-packages.

Kind regards

---

