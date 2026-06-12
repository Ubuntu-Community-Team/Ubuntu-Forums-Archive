---
title: "Xubuntu No Taskbar and Can't Log Out"
date: 2021-05-25
forum: Desktop Environments
---

### Post by anthonyhw3 on 2021-05-25
I have reinstalled my entire Ubuntu 20.04.2 LTS 2 times and each time, when I use
```
sudo apt-get install xubuntu-desktop
```
to install it, I reset my machine and I don't have a taskbar at the bottom of my screen and I can't log and have to use the
```
xfce4-session-logout
```
command to log out and switch desktop environments. Anybody know what could be causing this?

---

### Post by dddman on 2021-05-25
Cannot be done in a running session.

> ```
sudo apt install --reinstall xubuntu-desktop
```

---

### Post by ajgreeny on 2021-05-25
Open a terminal and run ***xfce4-panel*** to see if it suddenly appears on your desktop or gives you an error of some sort.

You should also run command ***xfce4-settings-manager*** to check in ***Session and Startup*** if the panel is shown in the **Current Session** tab and in the **Application Autostart** list.  It should be in both.

If you want to use xubuntu-desktop why not install Xubuntu rather than Ubuntu?
It will normally be much simpler to deal with a single DE.

---

### Post by ajgreeny on 2021-05-25
Another sudden thought!
After installing the xubuntu-desktop and logging out of Ubuntu which you had before, you now need to change to the Xubuntu session in the login screen; accept the user shown probably in the box then go to the cog that shows in the login box to choose Xubuntu.  That should give you the full Xubuntu desktop and default session of Xubuntu.

If you already did that, then use the ideas in my post above to help check what's going on.

---

### Post by Autodave on 2021-05-25
Hmmm.  Maybe I am missing something here, but I am running xubuntu and my task bar has always been at the top of the screen.....not the bottom.

---

### Post by ajgreeny on 2021-05-25
Good point autodave, I did not think about that as I prefer my panel at the bottom, however, you may be correct.

@ anthonyhw3
Do you have no panel anywhere?  If there is a panel somewhere on the desktop there will be either **Applications menu** or **Whisker menu** or you can add one or both of those which give you a normal Logout/Shutdown option.

---

### Post by deadflowr on 2021-05-25
As the OP mentions switching desktops I wonder what desktops are actually installed and from which do they intend to switch to and from?

---

### Post by david504 on 2021-06-08
if it was missing in xfce then:
[I]sudo apt-get install xfce4-panel xfce4-whiskermenu-plugin 
[/I]


But if it is the unity-greeter is confusing them and they must be used to lightdm greeter and the greeter don't have the taskbar on the top of the screen
so:
[I]sudo apt-get purge unity-greeter
sudo apt-get install  lightdm-gtk-greeter

[/I]

---

