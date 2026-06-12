---
title: "Upgrade to 20.04 now screen is on all the time?"
date: 2020-11-24
forum: Desktop Environments
---

### Post by rsteinmetz70112 on 2020-11-24
I recently did a do-release-upgrade to a 18.04 :TS desktop and everything went OK, except after the upgrade the screen stays on all the time. I have checked settings and it is set to blank the screen after 10 minutes, but doesn't . I have updated and upgraded and get not errors or packaged left behind. I'm wondering what may be going on. The machine does have an Nvidia GPU and the Nvidia drivers are installed and appera to be working.

---

### Post by rsteinmetz70112 on 2020-11-24
I discovered that 18.04 had been using NVIDIA-450 but 20.04 recommends NVIDIA-455. I removed the former and installed the latter and the problem persists.

---

### Post by rsteinmetz70112 on 2020-11-26
I've now found that I am running the lighdm display manager. Itried to switch to gdm3 and it wouldn't load correctly. 
Not sure if taht would have cangeed anything butit appras to be related to a screen locking issue with lightdm.

---

### Post by rsteinmetz70112 on 2020-11-26
I've located the ```
gnome-screensaver command -a
```
It doesn't appear to work although the command seems to be running
```
ps -df|grep gnome-screensaver
root        3272    3262  0 22:26 pts/0    00:00:00 grep --color=auto gnome-screesaver
```
However the gnome screensaver-preferences command does not appear to be present:

```
# gnome-screensaver-preferences
gnome-screensaver-preferences: command not found
```

I found the preferences are stored in the home directory of the user, in the $HOME/. xscreensaver file.
That file exists on my machine.

It refers to a programs called xscreensaves which is not installed, but can be installed.

Is it necessary?

---

### Post by rsteinmetz70112 on 2020-11-27
Looking further I've found a reference to the gnome shell have it's own screensaver.
I an article with configuration details  [https://www.thegeekdiary.com/how-to-customize-the-screensaver-options-in-gnome-on-centos-rhel-7/](https://www.thegeekdiary.com/how-to-customize-the-screensaver-options-in-gnome-on-centos-rhel-7/)
it refers to a directory /etc/dconf/db/local.d/00-screensaver which doesn't exist on my Ubuntu 20.04 computer. /etc/dconf/db/ does exist.

---

### Post by rsteinmetz70112 on 2020-11-30
```
xset -display :0.0 dpms force off
```

will turn the display off 

```
ctrl-c 
```will turn it back on.

---

### Post by rsteinmetz70112 on 2020-11-30
OK

I ran:
```
apt purge gdm3
apt purge lightdm
apt install gdm3
reboot
```

That seems to have fixed the problem with screen blanking. apparently screen blanking doesn't work with lightdm.
There seems to be a remaining problem.

# dpkg --configure -a
```
Setting up xcursor-themes (1.0.6-0ubuntu1) ...
update-alternatives: error: alternative path /etc/X11/cursors/core.theme doesn't exist
dpkg: error processing package xcursor-themes (--configure):
 installed xcursor-themes package post-installation script subprocess returned error exit status 2
Errors were encountered while processing:
 xcursor-themes
```

I added several directories and now there are no errors.

---

